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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

A-Alpha Bio is a Seattle biotechnology company that measures, predicts and engineers protein-protein
interactions. Its experimental platform **AlphaSeq** reprograms yeast mating to quantify millions of protein-protein
binding affinities in a single experiment; its computational platform **AlphaBind** predicts and optimizes
antibody-antigen binding from sequence. In July 2026 the company launched **Atlas**, a data platform publishing
ML-ready protein interaction "Data Blocks" for licensing, custom on-demand data generation, and a quarterly-release
consortium whose founding members include GSK, Boltz, Cradle and Dyno Therapeutics.

## API surface

Atlas is backed by a public HTTP API — the **Atlas Data Product API** at `https://api.atlas.aalphabio.com`, which
serves a live OpenAPI 3.1.0 document at `/openapi.json`. Nine read operations over Data Blocks. Dataset discovery,
dataset metadata and structured Data Cards answer **anonymously**; CSV data, CSV schemas and structure (`.cif`) files
require a bearer token issued through AWS Cognito sign-in.

The API is not linked from any A-Alpha Bio documentation — it was found by reading the preconnect hint in the Atlas
web app's HTML shell. There is no developer portal, no `/llms.txt`, no `/.well-known/` document, no MCP server, no
agent card, no status page and no changelog.

- Website — https://www.aalphabio.com/
- Atlas — https://atlas.aalphabio.com/
- GitHub — https://github.com/A-Alpha-Bio
- Blog — https://aalphabio.substack.com/
