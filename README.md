# A-Alpha Bio

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

A-Alpha Bio is a Seattle biotechnology company, founded in 2017 out of the University of Washington's Institute for Protein Design and Center for Synthetic Biology, that measures, predicts and engineers protein-protein interactions. Its experimental platform AlphaSeq reprograms yeast mating to quantify millions of protein-protein binding affinities in a single experiment, and its computational platform AlphaBind is a domain-specific deep-learning model trained on hundreds of millions of those affinity measurements to predict and optimize antibody-antigen binding from sequence. In July 2026 the company launched Atlas, a web platform and data ecosystem that publishes ML-ready protein interaction "Data Blocks" for licensing, custom on-demand data generation, and a quarterly-release Atlas Consortium whose founding members include GSK, Boltz, Cradle and Dyno Therapeutics. Atlas is backed by a public HTTP API — the Data Product API at api.atlas.aalphabio.com — which serves dataset discovery, dataset metadata and structured Data Cards anonymously, and gates CSV data, CSV schemas and structure (.cif) files behind a bearer token issued through AWS Cognito sign-in.

**Areas:** protein-interactions · Biotechnology · Drug Discovery · Antibody Engineering · Synthetic Biology · Machine Learning · Training Data · Data Licensing · Life Sciences · Datasets · Protein Design · Bioinformatics

## A-Alpha Bio on APIs.io

Everything profiled for A-Alpha Bio is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/a-alpha-bio/](https://apis.io/providers/a-alpha-bio/)** — or go straight to one of the APIs or properties below.

### APIs (1)

- [A-Alpha Bio Datasets API](https://apis.io/apis/a-alpha-bio/a-alpha-bio-datasets-api/) — The Datasets API from A-Alpha Bio — 9 operation(s) for datasets.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [a-alpha-bio-mcp.yml](https://apis.io/servers/a-alpha-bio/a-alpha-bio-mcp-yml/)

#### JSON Schema (3)

The data models the API reads and writes.

- [DatacardResponse](https://apis.io/schemas/a-alpha-bio/a-alpha-bio-datacard/)
- [DatasetSchemaResponse](https://apis.io/schemas/a-alpha-bio/a-alpha-bio-dataset/)
- [DatasetItem](https://apis.io/schemas/a-alpha-bio/a-alpha-bio-dataset-item/)

#### Examples (3)

Example requests and responses.

- [A Alpha Bio Get Dataset Datacard Response](https://apis.io/examples/a-alpha-bio/a-alpha-bio-get-dataset-datacard-response/)
- [A Alpha Bio Get Dataset Response](https://apis.io/examples/a-alpha-bio/a-alpha-bio-get-dataset-response/)
- [A Alpha Bio List Datasets Response](https://apis.io/examples/a-alpha-bio/a-alpha-bio-list-datasets-response/)

#### Collections (1)

Postman and Open Collection request collections.

- [A Alpha Bio Datasets API](https://apis.io/collections/a-alpha-bio/open-a-alpha-bio-datasets-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [A Alpha Bio Atlas Datasets Overlay](https://apis.io/overlays/a-alpha-bio/a-alpha-bio-atlas-datasets-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [A Alpha Bio Authentication](https://apis.io/security/a-alpha-bio/a-alpha-bio-authentication/)
- [A Alpha Bio Domain Security](https://apis.io/security/a-alpha-bio/a-alpha-bio-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.aalphabio.com/)
- [Sign up](https://atlas.aalphabio.com/)
- [Support](https://www.aalphabio.com/contact/)
- [Blog](https://aalphabio.substack.com/)
- [Terms of service](https://www.aalphabio.com/terms-of-service/)
- [Privacy policy](https://www.aalphabio.com/privacy-notice/)
- [GitHub](https://github.com/A-Alpha-Bio)

## API Evangelist rating

**Kin Score 33.4** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 79.5 |
| Contract quality | 55.4 |
| Contract governance | 4.5 |
| Operational transparency | 2.6 |
| Developer ergonomics | 28.0 |
| Access clarity | 21.1 |

**Agent readiness 27.1** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | verified |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 18.4** — Health

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/a-alpha-bio/](https://apis.io/providers/a-alpha-bio/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for A-Alpha Bio: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/a-alpha-bio/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
