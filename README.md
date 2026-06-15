# LeanData (leandata)

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
