---
layout: default
title: "Hosted MCP and agent search"
---

# Hosted MCP and agent search

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Endpoint

`POST https://<app-host>/api/mcp/<projectId>/mcp`

The existing route implements JSON-RPC initialize, tools/list and tools/call. Validate it against the MCP SDK/clients before claiming full Streamable HTTP compatibility. A successful handshake alone does not prove protected tool calls work.

## Documentation tools

| Tool | Purpose |
| --- | --- |
| list_documentation_pages | List saved pages and source URLs |
| get_documentation_page | Read a selected saved page |
| search_documentation | Return ranked sections with breadcrumbs and source URLs |
| get_documentation_overview | Summarize the corpus and provide its index |
| read_full_documentation | Retrieve bounded broad context when needed |
| ask_documentation | Optional OpenRouter answer grounded in retrieved sources |

These six existing tool names are the baseline. Custom API tool generation is secondary; no fixed total-tool promise. The release's primary tool surface reads documentation and does not execute source-vendor business operations.

## Agent use

An agent can call search_documentation directly through its MCP client. A framework may expose a local `search_docs` wrapper that forwards to it; that alias is a proposed convenience, not an additional deployed REST API. Search should return useful source content without requiring AI synthesis.

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/call",
  "params": {
    "name": "search_documentation",
    "arguments": { "query": "webhook signature verification", "limit": 5 }
  }
}
```

## Authentication

Send `Authorization: Bearer <project-token>`. The existing X-Docs4LLM-Token header is a compatibility path. Query-string tokens are not supported. App login, provider API authorization and MCP read access are separate.

Target lifecycle: owner-only issuance -> show raw token once -> store hash and project scope -> authenticate each protected request -> revoke or replace without recrawling. Never populate public manifests, logs or ordinary project JSON with tokens. Existing artifact storage/delivery must be migrated before this lifecycle is advertised as shipped.

## Editor configuration

Cursor-style configuration:

```json
{
  "mcpServers": {
    "myDocs": {
      "url": "https://<app-host>/api/mcp/<projectId>/mcp",
      "headers": { "Authorization": "Bearer <project-token>" }
    }
  }
}
```

For VS Code `.vscode/mcp.json`, use top-level `servers` rather than `mcpServers` or an extra `mcp` wrapper. Configure sensitive values through secure input prompts. Test the installed client version and its supported header/transport configuration.

An OAuth client-registration prompt indicates an OAuth flow; it is not proof of failed random token generation. Check domain, client config and actual requests. Browser-based MCP OAuth is deferred and is not implemented by switching the website login provider.

See [VS Code's reference](https://code.visualstudio.com/docs/agents/reference/mcp-configuration). Registry listing is optional discovery metadata; it neither issues access tokens nor proves the endpoint is usable.
