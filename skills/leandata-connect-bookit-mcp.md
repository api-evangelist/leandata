---
name: Connect an AI client to the LeanData BookIt MCP server
description: >-
  Authorize and connect an MCP client to LeanData's hosted BookIt MCP server so an agent can read
  availability and manage meetings under the caller's BookIt permission set, with routing rules,
  pool fairness and SLA logic enforced server-side.
api: mcp/leandata-mcp.yml
apis:
  - mcp/leandata-mcp.yml
operations:
  - POST https://mcp.leandata.com/mcp
  - GET https://mcp.leandata.com/.well-known/oauth-protected-resource
  - GET https://mcp.leandata.com/.well-known/oauth-authorization-server
generated: '2026-08-13'
method: generated
source: https://mcp.leandata.com/.well-known/ + https://www.leandata.com/resources/leandatas-bookit-mcp/
---

# Connect an AI client to LeanData BookIt MCP

LeanData ships a hosted, remote MCP server for BookIt. It is labelled **BETA** on LeanData's own
scheduling page. This is the only LeanData surface with machine-readable discovery metadata.

## Endpoint

```
https://mcp.leandata.com/mcp
```

Remote HTTP transport. There is no npx package and no local stdio server — an agent reaches this
URL directly once it holds a token.

## Discovery

An unauthenticated request returns `401` with:

```
WWW-Authenticate: Bearer resource_metadata="https://mcp.leandata.com/.well-known/oauth-protected-resource"
```

Follow it. The RFC 9728 document names the resource and its authorization server; the RFC 8414
document at `/.well-known/oauth-authorization-server` gives you everything else:

| Field | Value |
|---|---|
| issuer | `https://mcp.leandata.com` |
| authorization_endpoint | `https://mcp.leandata.com/authorize` |
| token_endpoint | `https://mcp.leandata.com/token` |
| registration_endpoint | `https://mcp.leandata.com/register` |
| grant_types | `authorization_code`, `refresh_token` |
| code_challenge_methods | `S256` |
| token_endpoint_auth_methods | `none` (public client) |
| scopes | `admin`, `user`, `partner`, `offline_access` |
| bearer_methods | `header` |

## Steps

1. **Register the client dynamically** at `/register` (RFC 7591). No pre-shared client secret is
   needed — the server is a public client and `token_endpoint_auth_methods_supported` is `none`.
2. **Start the authorization-code flow with PKCE** (`S256` is the only challenge method offered).
   Request `offline_access` alongside your role scope if you need a refresh token.
3. **Authenticate as one of two identities.**
   - *Salesforce OAuth* — for LeanData admins and reps. LeanData detects the caller's BookIt
     permission set after login.
   - *One-time code* — for external partners or AI agents with no Salesforce credentials in the
     org. An email address and a permission set are assigned in advance by the customer.
4. **Exchange the code at `/token`** and send the result as `Authorization: Bearer <token>`.
5. **List the tools.** `POST /mcp` with `{"jsonrpc":"2.0","id":1,"method":"tools/list"}` and
   `Accept: application/json, text/event-stream`. Read the real tool names and `inputSchema` from
   the response — do not assume them. The tool set you see is filtered by your permission set, so
   an admin and a rep receive different lists from the same server.

## What the server is documented to do

Admin-side: view cancelled meetings by pool, reason or date range; check real-time availability
across users and pools by meeting type; identify reps who have not connected their calendars;
manage cancellations, rescheduling and host swaps. Rep-side: look up upcoming meetings and
conference details; view own meetings, pipeline and availability; access own profile and
conferencing setup; mark no-shows and trigger the credit-back process; retrieve booking links.

## What it enforces

Every action taken through the server respects the org's routing rules, pool fairness settings and
SLA logic, and the tool list is filtered by the caller's BookIt permission set. The scopes are the
outer bound; the effective permission comes from Salesforce.

## Caveats

- Scope semantics are not published. `admin`, `user` and `partner` are discoverable names with no
  documented grant list, so least-privilege requests are guesswork.
- No published rate limit and no rate-limit response headers on this host.
- Several MCP capabilities have no REST counterpart, and the core REST write path (creating a
  meeting) is not named as an MCP capability. See `mcp/leandata-tool-crosswalk.yml`.

Cross-references: `mcp/leandata-mcp.yml`, `scopes/leandata-scopes.yml`,
`authentication/leandata-authentication.yml`.
