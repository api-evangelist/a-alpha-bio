---
name: load-data-block-into-pandas
description: >-
  Load a licensed A-Alpha Bio Atlas Data Block into a pandas DataFrame with the provider's own column schema, and
  pull its structure (.cif) files. Use when preparing Atlas protein-protein interaction data for model training or
  benchmarking. Requires an Atlas bearer token.
api: openapi/a-alpha-bio-atlas-datasets-openapi.yml
base_url: https://api.atlas.aalphabio.com
auth: HTTP bearer JWT (AWS Cognito access token) — required for every operation in this skill
operations:
  - getDataset
  - getDatasetSchema
  - getDatasetData
  - listDatasetStructures
  - getDatasetStructure
  - downloadDatasetStructures
generated: '2026-08-06'
method: generated
source: openapi/a-alpha-bio-atlas-data-product-openapi-original.json
---

# Load an Atlas Data Block

Every operation here is entitlement-gated. Without `Authorization: Bearer <token>` they return
`401 {"detail":"Missing token"}`. Get the token by signing in to https://atlas.aalphabio.com/ (or, for a terminal
session, the login-code flow at https://atlas.aalphabio.com/cli-login). A token that is present but invalid does not
raise on the anonymous-readable operations — it silently yields an empty catalogue — so verify entitlement on a gated
operation before assuming a block is unlicensed.

## 1. Pin the version — `getDataset`

```
GET /api/v1/datasets/{id}
```

Read `dataset.version` and use it explicitly on every subsequent call. **Omitting `version` resolves to latest**,
which means the same script run twice across a dataset re-release silently trains on different data. Pin it.

Also read `dataset.modes[]` — each entry is `{name, file_type}`. Observed modes are `source` (raw experimental
output) and `ml` (model-ready). Pick one; `ml` is normally what you want for training.

## 2. Get the column schema — `getDatasetSchema`

```
GET /api/v1/datasets/{id}/schema?mode=ml&version=1
```

Returns `{"dtype": {column: pandas-dtype}, "parse_dates": [column, ...]}` — deliberately shaped so it unpacks
straight into `pandas.read_csv`. Use it; do not infer dtypes.

## 3. Get the data URL — `getDatasetData`

```
GET /api/v1/datasets/{id}/data?mode=ml&version=1&redirect=false
```

By default this operation answers **302 to a pre-signed S3 URL**. Pass `redirect=false` to get
`{"url": "..."}` as JSON instead, which is what you want when you need the URL as a value rather than a follow.
`max_rows` caps the number of rows inside the CSV — use it to sample a large block before committing to the full
pull. It is a payload-size control, not pagination; there is no offset or cursor.

Put the three together:

```python
import requests, pandas as pd

BASE = "https://api.atlas.aalphabio.com"
H = {"Authorization": f"Bearer {token}"}
dataset_id, mode = "ab1001", "ml"

meta = requests.get(f"{BASE}/api/v1/datasets/{dataset_id}", headers=H).json()["dataset"]
version = meta["version"]                                   # pin it

schema = requests.get(f"{BASE}/api/v1/datasets/{dataset_id}/schema",
                      headers=H, params={"mode": mode, "version": version}).json()

url = requests.get(f"{BASE}/api/v1/datasets/{dataset_id}/data",
                   headers=H,
                   params={"mode": mode, "version": version, "redirect": "false"}).json()["url"]

df = pd.read_csv(url, **schema)                             # dtype + parse_dates come from the provider
```

The pre-signed URL expires — fetch it immediately before reading, do not cache it.

## 4. Structures — `listDatasetStructures`, `getDatasetStructure`, `downloadDatasetStructures`

```
GET /api/v1/datasets/{id}/structures?version=1                    -> {"files": ["...cif", ...]}
GET /api/v1/datasets/{id}/structures/{filename}?version=1         -> one file's content
GET /api/v1/datasets/{id}/structures/download?version=1           -> {"url": "<pre-signed zip>"}
```

Check `dataset.structure_count` first — many blocks ship zero structures and the list will be empty. For anything
more than a handful of files, take the zip: one pre-signed URL beats N round trips, and there is no documented rate
limit to rely on.

## Rules

- **Pin `version` on every call in a pipeline.** This is the single biggest reproducibility trap in this API.
- Keep `mode` consistent between the schema call and the data call — they are separate S3 objects
  (`data.<mode>.csv.gz` / `data.<mode>.schema.json`) and mixing them mismatches columns.
- Errors are **not** RFC 9457: `{"detail": "..."}` on 400/401/404, and an **array** on 422. Branch on the type.
- `404` on data/schema/structures can mean "does not exist for this mode", not just "no such dataset" — re-check
  `modes[]` before concluding the block is missing.
- No rate-limit headers, no `Retry-After`, no documented 429. Serialise your requests and back off on any non-2xx.
- Read `datacard.ml.recommended_splits` and `datacard.bio.considerations` before training. See
  skills/a-alpha-bio-browse-atlas-catalog.md.
