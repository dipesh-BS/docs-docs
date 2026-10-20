---
layout: default
title: "Connect Cursor"
description: "Connect Cursor for the hosted docs4llm release."
category: "Guides"
order: 37
---

# Connect Cursor

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Use the project's hosted endpoint and a valid project connection token. In Cursor's MCP configuration, add a server under mcpServers:

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

Replace placeholders with the owner-issued values and keep populated configs private. Reload the MCP connection, check tools/list, then ask the assistant to search the docs. Test the installed client version before advertising one-click installation.
