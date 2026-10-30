# LeanData

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

LeanData is a Sunnyvale, California revenue orchestration platform built on the Salesforce ecosystem. The company is best known for inventing lead-to- account matching and lead routing for B2B revenue teams; its managed package on the Salesforce AppExchange has been deployed by more than 1,000 B2B companies including Uber, Palo Alto Networks, Shopify, Zoom, New Relic, Snowflake, and DocuSign. The current platform spans four product lines — Orchestration (lead/contact/account routing, deduplication, SLAs, signal workflows), BookIt (forms, handoff, and links-based scheduling), Buying Groups (multi-stakeholder pipeline and engagement), and Revenue Insights (reporting and analytics). LeanData exposes four developer APIs that wrap the platform's core capabilities — the Matching API (real-time lead / contact / account identification from external systems), the Round Robin API (advanced weighted distribution, working hours, and vacation-aware assignment), the BookIt API (scheduling inputs, availability, and meeting CRUD for custom UIs), and the Graph API (one-time routing and routing-graph metadata for custom orchestration). The Matching and Round Robin APIs are Salesforce-native and dispatched through the managed package's Apex REST endpoint at /services/apexrest/LeanData/LeanDataAPI, authenticated with the customer's own Salesforce OAuth 2.0 Connected App; BookIt and Graph are hosted at api.leandata.com behind AWS API Gateway and authenticated with a server-side API key in an X-Api-Key header. Since the Q2 2026 release LeanData also runs a hosted BookIt MCP server at https://mcp.leandata.com/mcp — currently labelled beta — which exposes BookIt scheduling and operational data to MCP-compatible AI clients under OAuth 2.1 with PKCE and dynamic client registration, with admin, user and partner scopes and tool visibility filtered by the caller's BookIt permission set. Developer documentation is published as a public Postman collection at docs.leandata.com. Commercial offerings are tiered across Standard, Advanced, Premium, and Enterprise editions of Orchestration plus BookIt scheduling products and Buying Groups, with implementation services billed separately.

**Areas:** Revenue Operations · Lead Routing · Lead to Account Matching · Salesforce · Sales Engagement · Sales Productivity · Marketing Operations · Scheduling · Meeting Booking · Account Based Marketing · Buying Groups · Signal Orchestration

## LeanData on APIs.io

Everything profiled for LeanData is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/leandata/](https://apis.io/providers/leandata/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [LeanData 🗓️ Availability API](https://apis.io/apis/leandata/leandata-availability-api/) — <p>The availability endpoints return meeting configuration and open time slots used to render booking pages or refresh availability. Depending on the…
- [LeanData Legacy (still supported) API](https://apis.io/apis/leandata/leandata-legacy-still-supported-api/) — <p>This section outlines the endpoints used to retrieve scheduling data for building a custom calendaring experience. Both endpoints return the same…
- [LeanData Matching API](https://apis.io/apis/leandata/leandata-matching-api/) — The Matching API from LeanData — 1 operation(s) for matching.
- [LeanData 📆 Meetings > Create API](https://apis.io/apis/leandata/leandata-meetings-create-api/) — <p>Use these endpoints to finalize and book meetings after a timeslot has been selected.</p> <p>⚠️ <strong>Important:</strong> You <strong>must</strong>…
- [LeanData 📆 Meetings > Manage API](https://apis.io/apis/leandata/leandata-meetings-manage-api/) — The 📆 Meetings > Manage API from LeanData — 1 operation(s) for 📆 meetings > manage.
- [LeanData 📆 Meetings > Retrieve API](https://apis.io/apis/leandata/leandata-meetings-retrieve-api/) — The 📆 Meetings > Retrieve API from LeanData — 2 operation(s) for 📆 meetings > retrieve.
- [LeanData One Time Routing API](https://apis.io/apis/leandata/leandata-one-time-routing-api/) — <p>This section describes the endpoints used to trigger 1x Routing for creating a custom orchestration experience, as well as to retrieve the status of the…
- [LeanData Retrieve Routing Graphs Information API](https://apis.io/apis/leandata/leandata-retrieve-routing-graphs-information-api/) — <p>This section outlines the endpoints used to retrieve Routing Graphs information for building a custom orchestration experience. The endpoint returns…
- [LeanData 🧠 Scheduling Inputs API](https://apis.io/apis/leandata/leandata-scheduling-inputs-api/) — The 🧠 Scheduling Inputs API from LeanData — 1 operation(s) for 🧠 scheduling inputs.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [LeanData BookIt MCP](https://apis.io/servers/leandata/leandata-bookit-mcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Leandata Agentic Access](https://apis.io/agentic-access/leandata/leandata-agentic-access/)

#### Collections (12)

Postman and Open Collection request collections.

- [LeanData BookIt 🗓️ Availability 🗓️ Availability 🗓️ Availability API](https://apis.io/collections/leandata/open-leandata-availability-api/)
- [LeanData BookIt API](https://apis.io/collections/leandata/open-leandata-bookit/)
- [LeanData Graph API](https://apis.io/collections/leandata/open-leandata-graph/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability Legacy (still supported) API](https://apis.io/collections/leandata/open-leandata-legacy-still-supported-api/)
- [LeanData Matching and Round Robin API](https://apis.io/collections/leandata/open-leandata-matching/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability Matching API](https://apis.io/collections/leandata/open-leandata-matching-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability 📆 Meetings > Create API](https://apis.io/collections/leandata/open-leandata-meetings-create-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability 📆 Meetings > Manage API](https://apis.io/collections/leandata/open-leandata-meetings-manage-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability 📆 Meetings > Retrieve API](https://apis.io/collections/leandata/open-leandata-meetings-retrieve-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability One Time Routing API](https://apis.io/collections/leandata/open-leandata-one-time-routing-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability Retrieve Routing Graphs Information API](https://apis.io/collections/leandata/open-leandata-retrieve-routing-graphs-information-api/)
- [LeanData BookIt 🗓️ Availability 🗓️ Availability 🧠 Scheduling Inputs API](https://apis.io/collections/leandata/open-leandata-scheduling-inputs-api/)

#### Overlays (9)

OpenAPI overlays, including conversational phrasing for each operation.

- [Leandata Availability Overlay](https://apis.io/overlays/leandata/leandata-availability-overlay/)
- [Leandata Legacy Still Supported Overlay](https://apis.io/overlays/leandata/leandata-legacy-still-supported-overlay/)
- [Leandata Matching Overlay](https://apis.io/overlays/leandata/leandata-matching-overlay/)
- [Leandata Meetings Create Overlay](https://apis.io/overlays/leandata/leandata-meetings-create-overlay/)
- [Leandata Meetings Manage Overlay](https://apis.io/overlays/leandata/leandata-meetings-manage-overlay/)
- [Leandata Meetings Retrieve Overlay](https://apis.io/overlays/leandata/leandata-meetings-retrieve-overlay/)
- [Leandata One Time Routing Overlay](https://apis.io/overlays/leandata/leandata-one-time-routing-overlay/)
- [Leandata Routing Graphs Overlay](https://apis.io/overlays/leandata/leandata-routing-graphs-overlay/)
- [Leandata Scheduling Inputs Overlay](https://apis.io/overlays/leandata/leandata-scheduling-inputs-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Leandata Authentication](https://apis.io/security/leandata/leandata-authentication/)
- [Leandata Domain Security](https://apis.io/security/leandata/leandata-domain-security/)
- [Leandata Trust Center](https://apis.io/security/leandata/leandata-trust-center/)
- [Leandata Vulnerability Disclosure](https://apis.io/security/leandata/leandata-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Leandata Scopes](https://apis.io/scopes/leandata/leandata-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Leandata Plans Pricing](https://apis.io/plans/leandata/leandata-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Leandata Rate Limits](https://apis.io/rate-limits/leandata/leandata-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Leandata Finops](https://apis.io/finops/leandata/leandata-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.leandata.com)
- [Documentation](https://docs.leandata.com)
- [Getting started](https://docs.leandata.com)
- [API reference](https://docs.leandata.com)
- [Pricing](https://www.leandata.com/pricing/)
- [Sign up](https://www.leandata.com/demo-request/)
- [Support](https://support.leandata.com)
- [Changelog](https://leandatahelp.zendesk.com/hc/en-us/sections/360002566353-Release-Notes)
- [Blog](https://www.leandata.com/blog/)
- [Security](https://trust.leandata.com/?itemUid=64c9680b-ef79-4c92-baa0-13b541954bef)
- [Compliance](https://trust.leandata.com/)
- [Trust centre](https://trust.leandata.com/)
- [Terms of service](https://www.leandata.com/terms-of-service/)
- [Privacy policy](https://www.leandata.com/privacy/)
- [GitHub](https://github.com/leandata)
- [Status](https://status.leandata.com)

## API Evangelist rating

**Kin Score 61.7** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.8 |
| Contract quality | 42.3 |
| Contract governance | 4.5 |
| Operational transparency | 50.0 |
| Developer ergonomics | 61.3 |
| Access clarity | 100.0 |

**Agent readiness 52.3** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | — |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/leandata/](https://apis.io/providers/leandata/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for LeanData: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/leandata/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
