---
layout: default
title: "API reference"
---

# API reference

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

The existing route surface below is the implementation baseline. Response fields must be checked against handlers during implementation; examples describe minimum intent rather than a frozen response schema.

| Route | Authentication | Purpose |
| --- | --- | --- |
| POST /api/convert | App session | Create a documentation conversion |
| GET /api/projects/{id} | Owner app session | Read redacted status, logs and artifacts |
| POST /api/projects/{id}/retry | Owner app session | Retry conversion |
| POST /api/mcp/{projectId}/mcp | Project/read-access token for protected tools | MCP JSON-RPC |
| POST /api/internal/pipeline-worker | Verified internal queue request | Background processing |

```http
POST /api/convert
Content-Type: application/json

{"url":"https://docs.example.com"}
```

Read the project identifier returned by the handler and poll its status. Do not assume `/api/projects/convert`, `/search`, `/ask`, `/pages` or `/full` REST aliases exist: use the MCP tools for retrieval.

## Planned additions

Owner-only issue/revoke/replace connection-token operations, job idempotency and richer crawl progress are required work, not documented as live endpoints. Define their request/response schemas alongside implementation. General project responses stay redacted; token issuance returns the raw credential once with no-store caching and owner authorization.

## Errors

Distinguish invalid URL, unauthenticated app user, forbidden project access, source/provider failure, empty corpus, invalid MCP token, not-ready project and rate limit. Preserve actionable safe messages without logging credentials or provider payload secrets. Implement and test consistent status codes rather than inferring them from UI labels.

See [MCP specification](MCP_SPEC.md) for agent requests and [implementation status](STATUS.md) for known gaps.
