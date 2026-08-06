---
name: browse-atlas-catalog
description: >-
  Browse the A-Alpha Bio Atlas catalogue of protein-protein interaction Data Blocks and read a block's Data Card,
  without any credentials. Use when asked what training data A-Alpha Bio publishes, which Data Block suits an
  antibody-engineering task, or what is inside a specific Atlas dataset.
api: openapi/a-alpha-bio-atlas-datasets-openapi.yml
base_url: https://api.atlas.aalphabio.com
auth: none required for these operations
operations:
  - listDatasets
  - getDataset
  - getDatasetDatacard
generated: '2026-08-06'
method: generated
source: openapi/a-alpha-bio-atlas-data-product-openapi-original.json
---

# Browse the Atlas catalogue

All three operations below answer **without an `Authorization` header**. Verified 2026-08-06.

## 1. List the catalogue — `listDatasets`

```
GET https://api.atlas.aalphabio.com/api/v1/datasets?include_locked=true&include_coming_soon=true
```

**Do not omit `include_locked=true`.** It defaults to `false`, and because every published Data Block is `locked`
(metadata public, data behind a license or subscription), the default call returns `{"objects":[]}` and looks like an
empty catalogue. Add `include_coming_soon=true` to also see teaser blocks that have metadata but no data yet, and
`all_versions=true` to see superseded versions instead of only the latest.

Response is `{"objects": [DatasetItem, ...]}`. There is **no pagination** — no cursor, no `next`, no `Link` header.
The whole collection comes back in one array.

Fields worth filtering on:

- `product_kind` — `consortium` | `licensable` | `exclusive` | `open-source`. This is the access model, not a topic.
- `tasks[]` — the ML tasks the block suits, e.g. `affinity prediction`, `cross-target generalization`, `optimization`.
- `binder` / `target[]` — molecule classes, e.g. `VHH` against `viral` targets.
- `a_size`, `alpha_size`, `total_ppi_count`, `unique_ppi_count`, `density` — the scale of the measurement grid.
- `structure_count` — how many `.cif` structure files ship with the block.
- `coming_soon` — true means no data exists yet for anyone. Do not recommend it as usable training data.

## 2. Read one block's metadata — `getDataset`

```
GET https://api.atlas.aalphabio.com/api/v1/datasets/{id}
GET https://api.atlas.aalphabio.com/api/v1/datasets/{id}?version=1
```

`id` is the block identifier from `objects[].id` (observed form: `ab` + block number, e.g. `ab1001`). Omitting
`version` resolves to latest. Returns `{"dataset": DatasetItem}`.

The `url` field deep-links into the Atlas web portal. Trust the value in the live response, not the example in the
specification — the specification's example still carries a legacy host.

## 3. Read the Data Card — `getDatasetDatacard`

```
GET https://api.atlas.aalphabio.com/api/v1/datasets/{id}/datacard
```

This is the substantive artifact. It returns three sub-documents:

- `exec` — `scientific_value`, `use_cases[]`, `differentiations[]`, `stat_subs`.
- `ml` — `noise_signals[]`, `recommended_splits`, `data_views[]`, and `schema_columns[]` (name/type/description per
  CSV column). `recommended_splits` is the provider's own guidance on how to split the block for training; read it
  before proposing your own split.
- `bio` — `biological_system`, `findings[]`, `considerations[]`, `figures[]`. Read `considerations[]` before drawing
  conclusions — it is where assay caveats live.

`ml.data_views[].mode` is the handle you pass as `mode` to the data and schema operations.

## Rules

- **Errors are not RFC 9457.** The envelope is `{"detail": "..."}`, except on `422` where `detail` is an **array** of
  `{type, loc, msg, input}`. Check the type before formatting it.
- `404 {"detail":"Dataset not found"}` means the id or the version does not exist. List first; do not guess ids.
- `422` means a query parameter failed coercion — booleans must be literal `true`/`false`. Read `detail[].loc` for
  which one.
- There are **no rate-limit headers and no documented 429**. Do not hammer the endpoint; the catalogue is small
  enough to fetch once and cache.
- There is **no request-id header**, so nothing to quote if you need support. Record the URL and timestamp yourself.
- The three operations here are read-only GETs. Nothing you do can mutate Atlas.
