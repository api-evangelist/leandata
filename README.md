# LeanData (leandata)

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

LeanData is a Sunnyvale, California revenue orchestration platform built on the Salesforce ecosystem. The company is best known for inventing lead-to- account matching and lead routing for B2B revenue teams; its managed package on the Salesforce AppExchange has been deployed by more than 1,000 B2B companies including Uber, Palo Alto Networks, Shopify, Zoom, New Relic, Snowflake, and DocuSign. The current platform spans four product lines — Orchestration (lead/contact/account routing, deduplication, SLAs, signal workflows), BookIt (forms, handoff, and links-based scheduling), Buying Groups (multi-stakeholder pipeline and engagement), and Revenue Insights (reporting and analytics). LeanData exposes four developer APIs that wrap the platform's core capabilities — the Matching API (real-time lead / contact / account identification from external systems), the Round Robin API (advanced weighted distribution, working hours, and vacation-aware assignment), the BookIt API (scheduling inputs, availability, and meeting CRUD for custom UIs), and the Graph API (one-time routing and routing-graph metadata for custom orchestration). The Matching and Round Robin APIs are Salesforce-native and dispatched through the managed package's Apex REST endpoint at /services/apexrest/LeanData/LeanDataAPI; BookIt and Graph are hosted at api.leandata.com and authenticated via OAuth 2.0 server-to-server flows. Commercial offerings are tiered across Standard, Advanced, Premium, and Enterprise editions of Orchestration plus BookIt scheduling products and Buying Groups, with implementation services billed separately.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/leandata/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/leandata/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Provider
- **Access:** 3rd-Party

## Tags

- Revenue Operations
- Lead Routing
- Lead to Account Matching
- Salesforce
- Sales Engagement
- Sales Productivity
- Marketing Operations
- Scheduling
- Meeting Booking
- Account Based Marketing
- Buying Groups
- Signal Orchestration
- Go to Market
- RevOps
- GTM
- CRM
- AppExchange

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### LeanData Matching API

Identify Salesforce Leads, Contacts, or Accounts from external systems in real time using LeanData's industry-best matching engine. Supports matched-lead lookup, duplicate-lead detection, all-duplicate-lead retrieval, related-lead inspection, duplicate-contact detection, and account matching and related-account lookup. Operations are dispatched via the managed package's Apex REST endpoint `/services/apexrest/LeanData/LeanDataAPI` against the customer's Salesforce instance, authenticated using a Salesforce OAuth 2.0 Connected App.

- **Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

#### Tags

- Matching
- Lead Matching
- Contact Matching
- Account Matching
- Deduplication
- Salesforce

#### Properties

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-matching-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/leandata-matching.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/leandata-matching.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LeanData Round Robin API

Assign Salesforce records using LeanData's advanced round-robin logic, including standard rotation, flexible/weighted distribution, working hours, vacation rules, and pool inspection. Also exposes one-time routing for ad-hoc record assignment. Like the Matching API, all operations are dispatched through the managed package's Apex REST endpoint `/services/apexrest/LeanData/LeanDataAPI` in the customer's Salesforce org.

- **Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

#### Tags

- Round Robin
- Routing
- Assignment
- Salesforce
- Lead Routing

#### Properties

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-matching-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/leandata-matching.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/leandata-matching.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LeanData BookIt API

Programmatic scheduling, availability lookup, and meeting management for LeanData BookIt. Retrieve scheduling inputs, fetch raw or routed availability, create and round-robin meetings, retrieve meetings by prospect or meeting ID, patch (reschedule) and delete (cancel) meetings. Power custom booking UIs with secure server-to-server access hosted at `https://api.leandata.com/v1`. Legacy `/v1/scheduling/route`, `/v1/scheduling/retrieve-info`, and `/v1/scheduling/retrieve-modification-info` endpoints remain supported for existing integrations.

- **Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

#### Tags

- Scheduling
- Meetings
- Availability
- BookIt
- Booking

#### Properties

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-bookit-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/leandata-bookit.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/leandata-bookit.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### LeanData Graph API

Retrieve routing-graph metadata and trigger LeanData One Time Routing from external systems to power custom orchestration experiences. The Graph API exposes `orchestration/v1/routing-graphs` for graph discovery (trigger nodes, edges, names) and `orchestration/v1/one-time-routing` plus `orchestration/v1/one-time-routing/{jobId}` for invoking and monitoring one-time routing jobs against a Salesforce org. Hosted at `https://api.leandata.com/orchestration/v1`.

- **Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

#### Tags

- Orchestration
- Routing
- Graph
- One Time Routing

#### Properties

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-graph-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/leandata-graph.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/leandata-graph.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://www.leandata.com)
- [Portal](https://docs.leandata.com)
- [Documentation](https://docs.leandata.com)
- [Documentation](https://api.leandatainc.com)
- [Support Portal](https://leandatahelp.zendesk.com)
- [Support Portal](https://support.leandata.com)
- [Changelog](https://leandatahelp.zendesk.com/hc/en-us/sections/360002566353-Release-Notes)
- [Pricing](https://www.leandata.com/platform/pricing/)
- [Plans](plans/leandata-plans-pricing.yml)
- [Rate Limits](rate-limits/leandata-rate-limits.yml)
- [Fin Ops](finops/leandata-finops.yml)
- [Product](https://www.leandata.com/platform/)
- [Product](https://www.leandata.com/platform/orchestration/)
- [Product](https://www.leandata.com/platform/bookit/)
- [Product](https://www.leandata.com/platform/buying-groups/)
- [Integrations](https://www.leandata.com/platform/integrations/)
- [Customers](https://www.leandata.com/customers/)
- [Training](https://www.leandata.com/learning-center/)
- [Training](https://www.leandata.com/certification/)
- [Resources](https://www.leandata.com/resources/)
- [Blog](https://www.leandata.com/blog/)
- [Forum](https://www.opsstars.com/)
- [App Exchange](https://appexchange.salesforce.com/listingDetail?listingId=a0N3000000B4HCREA3)
- [Company](https://www.leandata.com/company/)
- [Careers](https://www.leandata.com/careers/)
- [Contact](https://www.leandata.com/contact/)
- [Newsroom](https://www.leandata.com/press/)
- [Trust Center](https://www.leandata.com/trust/)
- [Privacy Policy](https://www.leandata.com/privacy-policy/)
- [Terms of Service](https://www.leandata.com/terms-of-use/)
- [LinkedIn](https://www.linkedin.com/company/leandatainc/)
- [Twitter](https://twitter.com/leandatainc)
- [YouTube](https://www.youtube.com/@leandatainc)
- [GitHub Organization](https://github.com/leandata)
- [Authentication](https://docs.leandata.com)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
