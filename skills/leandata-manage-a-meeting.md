---
name: Retrieve, reschedule and cancel a LeanData BookIt meeting
description: >-
  Look up a prospect's meetings, read one meeting's details, then reschedule or cancel it
  through the BookIt API — including the re-fetch-availability step a reschedule requires and
  the retry hazards on a non-idempotent write surface.
api: openapi/leandata-meetings-retrieve-api-openapi.yml
apis:
  - openapi/leandata-meetings-retrieve-api-openapi.yml
  - openapi/leandata-meetings-manage-api-openapi.yml
  - openapi/leandata-availability-api-openapi.yml
operations:
  - GET /v1/meetings
  - GET /v1/meeting/:meetingId
  - POST /v1/scheduling/fetch-availability
  - PATCH /v1/meeting/:meetingId
  - DELETE /v1/meeting/:meetingId
generated: '2026-08-13'
method: generated
source: openapi/*.yml + https://docs.leandata.com
---

# Retrieve, reschedule and cancel a LeanData BookIt meeting

Operations are named by METHOD and PATH because the LeanData specs declare no `operationId`.

## Before you start

- Base URL `https://api.leandata.com`; `X-Api-Key` header on every call; HTTPS only.
- One object per request — no bulk updates.
- Times are **epoch milliseconds** in this domain.

## Steps

1. **Find the meeting.**
   `GET /v1/meetings?prospectEmail=<email>` returns an array of the prospect's meetings, each with
   `id`, `title`, `status` (`confirmed` / `canceled`), `scheduledTime`, `organizer_email` and
   `attendees[]`. There is no pagination parameter — you get the whole set.

2. **Read one meeting.**
   `GET /v1/meeting/{meetingId}` returns the same shape for a single meeting including conference
   details. Missing id → `404 {"error":"Meeting not found"}`.

3. **To reschedule, re-fetch availability first.**
   `POST /v1/scheduling/fetch-availability` identified by exactly one of `linkId`, `meetingId` or
   `token`. For an existing meeting, use `meetingId` — a one-shot booking `token` is already spent
   and will return `400 {"error":"Meeting has already been booked. Please use meetingId or
   eventId (legacy) to refetch availability."}`.
   Other failures:
   - `400 {"error":"Validation Error: Missing required parameter: linkId, meetingId or token"}`
   - `404 {"error":"link not found"}`
   - `404 {"error":"Validation Error: Unsupported link type. Please provide the linkId of a single meeting type BookIt Link."}` — note this validation error is returned as a 404.

4. **Apply the change.**
   `PATCH /v1/meeting/{meetingId}` with the new time drawn from the availability response in step 3.
   Never construct a time yourself — a slot that was free a moment ago may not be.

5. **Or cancel.**
   `DELETE /v1/meeting/{meetingId}`. Confirm by re-reading the meeting; `status` becomes `canceled`.

## Retries and idempotency

There is no idempotency key on this surface. `DELETE` is naturally idempotent, but `PATCH` is not
guarded, and a timed-out reschedule cannot be safely replayed. On any timeout, re-read with
`GET /v1/meeting/{meetingId}` and compare `scheduledTime` before deciding whether to send again.

## Correlating with support

LeanData returns no request-id of its own. The AWS API Gateway in front of the API does return
`x-amzn-requestid` on every response — capture it and quote it to `support@leandata.com`, since
it is the only per-request correlation handle available.

Cross-references: `errors/leandata-problem-types.yml`, `conventions/leandata-conventions.yml`,
`data-model/leandata-data-model.yml`.
