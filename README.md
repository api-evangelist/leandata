# LeanData (leandata)

LeanData is a Sunnyvale, California revenue orchestration platform built on the Salesforce ecosystem. The company invented lead-to-account matching and lead routing for B2B revenue teams; its managed package on the Salesforce AppExchange has been deployed by more than 1,000 B2B companies including Uber, Palo Alto Networks, Shopify, Zoom, New Relic, Snowflake, and DocuSign. The current platform spans four product lines — Orchestration (lead/contact/account routing, deduplication, SLAs, signal workflows), BookIt (forms, handoff, and links-based scheduling), Buying Groups (multi-stakeholder pipeline and engagement), and Revenue Insights (reporting and analytics). LeanData exposes four developer APIs that wrap the platform's core capabilities.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/leandata/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Revenue Operations, Lead Routing, Lead to Account Matching, Salesforce, Sales Engagement, Sales Productivity, Marketing Operations, Scheduling, Meeting Booking, Account Based Marketing, Buying Groups, Signal Orchestration, Go to Market, RevOps, GTM, CRM, AppExchange

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### LeanData Matching API
Identify Salesforce Leads, Contacts, or Accounts from external systems in real time using LeanData's industry-best matching engine. Supports matched-lead lookup, duplicate-lead detection, all-duplicate-lead retrieval, related-lead inspection, duplicate-contact detection, and account matching and related-account lookup. Operations are dispatched via the managed package's Apex REST endpoint `/services/apexrest/LeanData/LeanDataAPI` against the customer's Salesforce instance, authenticated using a Salesforce OAuth 2.0 Connected App.

**Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-matching-openapi.yml)
- [Naftiko Capability — Matching](capabilities/matching-records.yaml)

### LeanData Round Robin API
Assign Salesforce records using LeanData's advanced round-robin logic, including standard rotation, flexible/weighted distribution, working hours, vacation rules, and pool inspection. Also exposes one-time routing for ad-hoc record assignment. Like the Matching API, all operations are dispatched through the managed package's Apex REST endpoint `/services/apexrest/LeanData/LeanDataAPI` in the customer's Salesforce org.

**Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-matching-openapi.yml)
- [Naftiko Capability — Round Robin](capabilities/round-robin-routing.yaml)

### LeanData BookIt API
Programmatic scheduling, availability lookup, and meeting management for LeanData BookIt. Retrieve scheduling inputs, fetch raw or routed availability, create and round-robin meetings, retrieve meetings by prospect or meeting ID, patch (reschedule) and delete (cancel) meetings. Power custom booking UIs with secure server-to-server access hosted at `https://api.leandata.com/v1`. Legacy `/v1/scheduling/route`, `/v1/scheduling/retrieve-info`, and `/v1/scheduling/retrieve-modification-info` endpoints remain supported for existing integrations.

**Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-bookit-openapi.yml)
- [Naftiko Capability — BookIt Scheduling](capabilities/bookit-scheduling.yaml)
- [Naftiko Capability — BookIt Meetings](capabilities/bookit-meetings.yaml)

### LeanData Graph API
Retrieve routing-graph metadata and trigger LeanData One Time Routing from external systems to power custom orchestration experiences. The Graph API exposes `orchestration/v1/routing-graphs` for graph discovery (trigger nodes, edges, names) and `orchestration/v1/one-time-routing` plus `orchestration/v1/one-time-routing/{jobId}` for invoking and monitoring one-time routing jobs against a Salesforce org. Hosted at `https://api.leandata.com/orchestration/v1`.

**Human URL:** [https://docs.leandata.com](https://docs.leandata.com)

- [Documentation](https://docs.leandata.com)
- [OpenAPI](openapi/leandata-graph-openapi.yml)
- [Naftiko Capability — Graph Orchestration](capabilities/graph-orchestration.yaml)

## Editions and Pricing

LeanData prices on a contact-sales basis with structure based on features, Salesforce users/queues, and objects routed. Implementation services are billed separately.

| Edition | Description |
|---|---|
| Orchestration Standard | Lead-to-account matching, basic routing rules, deduplication, audit logs, managed reports |
| Orchestration Advanced (Best Value) | Adds routing for contacts and accounts, signal-driven workflows, enhanced dedupe, SLA dashboards, sales engagement and enrichment integrations |
| Orchestration Premium | Routing for any Salesforce object, advanced territory matching, scheduled automations, cross-object assignment, channel/partner GTM |
| Orchestration Enterprise | Full Premium plus dedicated AM and CSM, solution consulting, sandbox/production support, flexible compliance |
| BookIt for Forms | Web-form booking with intelligent CRM matching |
| BookIt Handoff | Automatic scheduling for team handoffs |
| BookIt Links | Personalized scheduling links for outreach |
| Buying Groups | Buying-group identification, journey orchestration, engagement alerts |

See [plans/leandata-plans-pricing.yml](plans/leandata-plans-pricing.yml), [rate-limits/leandata-rate-limits.yml](rate-limits/leandata-rate-limits.yml), and [finops/leandata-finops.yml](finops/leandata-finops.yml) for the machine-readable commercial surface.

## Common Resources

- [Website](https://www.leandata.com)
- [API Documentation Portal](https://docs.leandata.com)
- [Legacy Matching API Docs](https://api.leandatainc.com)
- [Help Center](https://leandatahelp.zendesk.com)
- [Support](https://support.leandata.com)
- [Pricing](https://www.leandata.com/platform/pricing/)
- [Integrations](https://www.leandata.com/platform/integrations/)
- [Customers](https://www.leandata.com/customers/)
- [Learning Center](https://www.leandata.com/learning-center/)
- [LeanData Certification](https://www.leandata.com/certification/)
- [OpsStars Community](https://www.opsstars.com/)
- [Salesforce AppExchange Listing](https://appexchange.salesforce.com/listingDetail?listingId=a0N3000000B4HCREA3)
- [GitHub Organization](https://github.com/leandata)
- [LinkedIn](https://www.linkedin.com/company/leandatainc/)
- [Twitter / X](https://twitter.com/leandatainc)
- [YouTube](https://www.youtube.com/@leandatainc)

## Authentication

- **Matching and Round Robin APIs** — Salesforce OAuth 2.0 via a customer-built Connected App. Calls are made against the customer's own Salesforce instance URL (`https://{instance}.my.salesforce.com/services/apexrest/LeanData/LeanDataAPI`) and inherit the connected user's Salesforce permissions.
- **BookIt API and Graph API** — OAuth 2.0 server-to-server tokens issued for a LeanData org, used as `Authorization: Bearer …` against `https://api.leandata.com`.

## Maintainer

- Kin Lane — kin@apievangelist.com
