---
name: Run LeanData one-time routing against a Salesforce object set
description: >-
  Trigger LeanData 1x Routing through the Graph API and poll the job to completion — including
  the silent-failure hazard LeanData documents, where an invalid FlowBuilder graph is accepted,
  processed, and fails with no error response.
api: openapi/leandata-one-time-routing-api-openapi.yml
apis:
  - openapi/leandata-retrieve-routing-graphs-information-api-openapi.yml
  - openapi/leandata-one-time-routing-api-openapi.yml
operations:
  - GET /orchestration/v1/routing-graphs
  - POST /orchestration/v1/one-time-routing
  - GET /orchestration/v1/one-time-routing/:jobId
generated: '2026-08-13'
method: generated
source: openapi/*.yml + https://docs.leandata.com
---

# Run LeanData one-time routing

Operations are named by METHOD and PATH because the LeanData specs declare no `operationId`.

## Before you start

- Base URL `https://api.leandata.com`; `X-Api-Key` header on every call; HTTPS only.
- Graph API keys are self-service for an org admin: **Settings > Admin > Authorization**.
- Published limit: 10,000 requests per second per API key. No rate-limit response headers are
  returned, so you cannot observe your remaining budget.
- Times in this domain are **ISO 8601 UTC** (unlike BookIt, which uses epoch milliseconds).

## Read this before you trigger anything

LeanData documents explicitly that **the API does not validate FlowBuilder graphs before
triggering routing**. If you invoke 1x Routing against an invalid or misconfigured graph, the
request is still accepted and processed — routing then fails silently and **no error response is
returned**. Verify the graph is live and working in the LeanData application before you call the
API, and always poll the job rather than treating the create response as success.

## Steps

1. **List the org's routing graphs.**
   `GET /orchestration/v1/routing-graphs` with `objectType` (Lead, Contact, Account, Opportunity,
   Case). Missing it → `400 {"error":"Validation Error: objectType is required."}`.
   Each graph returns `id`, `name`, `isLive`, `triggerNodeEdges`, `lastDeployedDate`,
   `lastModifiedBy` and `businessUnitId`.
   Select on `isLive: true`. Note the field `canGraphBeOveridden` is spelled with a single `r`
   in the payload — match the typo.

2. **Pick the trigger node and edge.**
   `triggerNodeEdges` is keyed by node name; each entry has `nodeType` (`TRIGGER` or
   `UPDATE TRIGGER`) and an `edges[]` array. The create request takes the same values in title
   case — `Trigger` / `Update Trigger` — so translate the casing.

3. **Trigger routing.**
   `POST /orchestration/v1/one-time-routing` with, at minimum, `objectType`, `condition` (a SOQL
   WHERE clause, e.g. `Title = 'CEO'`), `graphName`, `nodeType` and `edgeName`.
   Optional: `allowDedupe` (default false), `businessUnitId` (default null), `orderBy`,
   `notificationsDisabled`.
   Missing condition → `400 {"error":"Validation Error: condition is required"}`.
   Success returns `{"result": {"condition", "nRecords", "jobId", "objectType"}}`. `nRecords` is
   a **string** here.

4. **Poll the job.**
   `GET /orchestration/v1/one-time-routing/{jobId}` returns `{"result": {"jobId", "status",
   "nRecordsProcessed", "successCount", "completedAt"}}`. `status` reaches `Complete`.
   `nRecordsProcessed` is an **integer** here — the same quantity that was a string on create.
   Compare `successCount` against `nRecordsProcessed`: a completed job with a shortfall is how a
   partially-failed routing run presents itself, since nothing is raised as an error.

5. **Encode your query parameters.** LeanData publishes a full percent-encoding table for the
   Graph API. In particular `+` must be sent as `%2B` or it is read as a space, and `&`, `#`, `%`,
   `'`, `"`, `?`, `/`, `:`, `;`, `=`, `,`, parentheses and brackets must all be encoded. Tilde is
   safe. A SOQL `condition` containing an apostrophe — which almost all of them do — is the case
   that bites first.

## Retries

No idempotency key. Re-sending a one-time-routing request runs routing again against live
Salesforce records. On a timeout, do not resend: you have no `jobId`, so query the LeanData audit
log (Q2 2026 unified audit logs, 15-minute sync) to establish whether the run happened before
issuing another.

Cross-references: `errors/leandata-problem-types.yml`, `rate-limits/leandata-rate-limits.yml`,
`data-model/leandata-data-model.yml`.
