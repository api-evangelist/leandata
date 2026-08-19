---
name: Book a meeting with LeanData BookIt
description: >-
  Take a prospect from a routing decision to a confirmed meeting using the LeanData BookIt API:
  discover the graph's required inputs, route and fetch availability, then book against the
  correct create endpoint. Covers the displayAllPoolAvailability branch that decides which
  create endpoint is legal.
api: openapi/leandata-scheduling-inputs-api-openapi.yml
apis:
  - openapi/leandata-scheduling-inputs-api-openapi.yml
  - openapi/leandata-availability-api-openapi.yml
  - openapi/leandata-meetings-create-api-openapi.yml
operations:
  - POST /v1/scheduling/retrieve-inputs
  - POST /v1/scheduling/route-and-fetch-availability
  - POST /v1/meeting
  - POST /v1/round-robin-meeting
generated: '2026-08-13'
method: generated
source: openapi/*.yml + https://docs.leandata.com
---

# Book a meeting with LeanData BookIt

The LeanData OpenAPI files carry no `operationId`, so every step below names the operation by
METHOD and PATH exactly as it appears in `paths` in the referenced spec.

## Before you start

- Base URL: `https://api.leandata.com`
- Auth: send `X-Api-Key: <key>` on every request. HTTPS only — HTTP is rejected.
- Keys are server-side only. Never place a BookIt key in browser code.
- BookIt keys are issued by the LeanData Solutions Engineering Team; there is no self-service.
- One object per request. The API does not support bulk operations.
- There is **no idempotency key**. See "Retries" below before you write any retry logic.

## Steps

1. **Discover what the customer's graph expects.**
   `POST /v1/scheduling/retrieve-inputs` with the prospect trigger node name.
   The response is `{ "name": <node>, "inputs": [ { "name", "type" } ] }` where `type` is one of
   `STRING`, `PHONE`, `DOUBLE`, `BOOLEAN`. Build your form or agent payload from this — the input
   set is per-customer and must not be hard-coded.
   Failure: `400 {"error":"Validation Error: No prospect trigger node found with name: ..."}`.

2. **Route the prospect and fetch availability.**
   `POST /v1/scheduling/route-and-fetch-availability`, supplying every required input from step 1.
   The response carries `routing` (`responseType`, `calendarLink`, `token`), `scheduling.meeting`
   (the meeting type: `name`, `duration`, `formFields`, `description`), and `pageInfo`.
   Common failures:
   - `400 {"error":"Validation Error: Missing required input: uid"}` — an input from step 1 is absent.
   - `400 {"error":"Invalid Node name provided"}`.
   - `400 {"error":"Please check the following users have the correct product access and their calendar tokens are valid: <sfdc user id>"}` — a configuration failure. Do not retry; report it.

3. **Read `pageInfo.displayAllPoolAvailability`. This decides the create endpoint.**
   LeanData documents this as mandatory and unpredictable — it is driven by the customer's
   scheduling graph and cannot be assumed ahead of time.
   - `true` → you **must** book with `POST /v1/round-robin-meeting`
   - `false` or `null` → you **must** book with `POST /v1/meeting`

4. **Book.**
   Send the selected slot plus the values for every `formFields[]` entry marked `required: true`.
   Times in the scheduling domain are **epoch milliseconds**, not ISO 8601.
   Failures to expect:
   - `400 {"error":"The selected time is no longer available."}` — the slot was taken between step 2 and step 4. Go back to step 2 and re-present fresh slots.
   - `400 {"error":"This link only allows one booking and has already been used."}`
   - `400 {"error":"Validation Error: Scheduled time is before the minimum booking notice"}`

5. **Confirm.** The created meeting has an opaque 52-character `id`, a `status` of `confirmed`,
   a `scheduledTime` of `{start_time, end_time}` in epoch ms, an `organizer_email`, and an
   `attendees[]` array whose `responseStatus` values follow the Google Calendar vocabulary
   (`accepted`, `needsAction`). Store the `id` — it is what every later operation uses.

## Retries

LeanData publishes no idempotency mechanism. A booking request that times out cannot be safely
replayed: the retry either creates a second meeting or returns "The selected time is no longer
available" / "This link only allows one booking and has already been used", and neither response
tells you which happened. On a timeout, **do not blind-retry**. Call `GET /v1/meetings?prospectEmail=<email>`
first and check whether the meeting already exists, then act on the answer.

## Tokens

`routing.token` is one-shot. Once a meeting has been booked against it, re-fetching availability
with the token returns `400 {"error":"Meeting has already been booked. Please use meetingId or
eventId (legacy) to refetch availability."}` — switch to `meetingId` from then on.

## Errors and conventions

Every BookIt failure is a flat `{"error": "<message>"}` with no code and no field pointer;
`Validation Error:` is the only machine-usable prefix. An unauthenticated call is intercepted by
AWS API Gateway ahead of LeanData and returns `{"message":"Unauthorized"}` instead — a different
envelope. Full catalog: `errors/leandata-problem-types.yml`. Cross-cutting semantics:
`conventions/leandata-conventions.yml`.
