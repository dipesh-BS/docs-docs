---
layout: default
title: "MCP API"
description: "MCP API for the hosted docs4llm release."
category: "API Reference"
order: 19
---

# MCP API

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Use POST /api/mcp/{projectId}/mcp with JSON-RPC and a valid project bearer token for protected tool calls.

```json
{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"search_documentation","arguments":{"query":"authentication","limit":5}}}
```

The existing route supports initialize, tools/list and tools/call. End-to-end transport/client compatibility must be tested. A successful initialize response alone does not validate credentials.
