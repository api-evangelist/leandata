---
name: Match a lead, contact or account with the LeanData Matching API
description: >-
  Identify a Salesforce Lead, Contact or Account from an external system in real time, and
  assign records with Round Robin, through the LeanData managed package's Apex REST endpoint in
  the customer's own Salesforce org.
api: openapi/leandata-matching-api-openapi.yml
apis:
  - openapi/leandata-matching-api-openapi.yml
operations:
  - POST /services/apexrest/LeanData/LeanDataAPI
generated: '2026-08-13'
method: generated
source: openapi/leandata-matching-api-openapi.yml + https://docs.leandata.com
---

# Match a lead, contact or account with LeanData

This API is **not** hosted by LeanData. It runs inside the customer's own Salesforce org, served
by the LeanData managed package's Apex REST service. Everything below reflects that.

## Before you start

- Host: `https://<your-instance>.my.salesforce.com` — the customer's Salesforce My Domain.
- Path: `/services/apexrest/LeanData/LeanDataAPI` (POST, always).
- Auth: a Salesforce OAuth 2.0 Connected App session, not a LeanData API key.
  1. Build a Connected App (client id, secret, redirect URL).
  2. Send the user to `https://login.salesforce.com/services/oauth2/authorize?response_type=code&client_id=...&redirect_uri=...`.
  3. Exchange the code at `https://login.salesforce.com/services/oauth2/token` for an access token,
     an instance URL and a refresh token.
  4. Refresh with `grant_type=refresh_token` when the access token expires.
- Provisioning: the customer authorizes the LeanData token from the LeanData tab in Salesforce,
  then asks their LeanData CSM to enable the Matching API for that Salesforce org id. Partners
  request access at `partners@leandatainc.com`.
- All documented operations require LeanData managed package version **1.500+**.

## The single-endpoint pattern

There is one path and one verb. The operation is selected by fields in the request body —
`category` plus `apiType` — plus a required `version` field documented as `2`. The documented
`apiType` values are:

| Domain | apiType | Returns |
|---|---|---|
| Lead | `matchedLead` | a single matched Lead using default tie-breakers and filters |
| Lead | `duplicateLead` | a single duplicate Lead |
| Lead | `allDuplicateLeads` | all duplicate Leads |
| Lead | `allRelatedLeads` | all Leads related to the company matched from the request |
| Contact | `duplicateContact` | a single duplicate Contact |
| Contact | `allDuplicateContacts` | all duplicate Contacts |
| Account | `matchedAccount` | a single matched Account using configured tie-breakers and filters |
| Routing | `roundRobin` | the next-up owner from a pool, with or without assigning the record, or pool details |

## Steps

1. **Decide the question.** Matching answers "does this person or company already exist in the
   CRM?"; Round Robin answers "who should own this record next?".

2. **Send the values you have.** LeanData requires no specific field, but accuracy scales with
   the number of data points. Recommended: company name, website and email for `matchedAccount`;
   person name for the duplicate Lead and Contact modes.

3. **Ask for the fields you want back.** The request names the desired return field values of the
   matched record(s). Any field on the matched object can be returned on request — so ask for the
   Salesforce ids and whatever your downstream flow needs, in one call.

4. **Handle the two documented failures.**
   - `{"message":"Session expired or invalid","errorCode":"INVALID_SESSION_ID"}` — refresh the
     Salesforce OAuth token. This is the Salesforce error envelope, with a machine-readable
     `errorCode`, and it is a different shape from every BookIt/Graph error.
   - `"No such column 'Favorite Food' on sobject of type Lead"` — a field named in your request or
     in your requested return values does not exist on that object. Verify the field's **API name**,
     not its label.

5. **Round Robin has three modes.** Standard assignment returns the next-up owner *and* assigns the
   Salesforce record. Flexible returns the next-up owner *without* assigning, and does not require a
   Salesforce record at all. Pool Information returns pool names and pool details. Choose
   deliberately — the first mutates CRM data, the second does not.

## Limits

There is no LeanData quota here. The call consumes the customer's **Salesforce** governor limits:
daily API request quotas per org edition, per-transaction CPU and heap limits, and concurrent
long-running Apex caps — shared with everything else in that org. Budget accordingly and see
`rate-limits/leandata-rate-limits.yml`.

## Retries

No idempotency key, and the Round Robin standard-assignment mode is a write against live CRM
records. Treat a timed-out `roundRobin` standard-assignment call as *possibly applied*: re-read
the record's owner before sending again.

Cross-references: `authentication/leandata-authentication.yml`, `errors/leandata-problem-types.yml`.
