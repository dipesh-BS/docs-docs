---
layout: default
title: "Connect VS Code"
description: "Connect VS Code for the hosted docs4llm release."
category: "Guides"
order: 38
---

# Connect VS Code

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

For a workspace .vscode/mcp.json file, use top-level servers and a secure input for the token:

```json
{
  "inputs": [
    { "type": "promptString", "id": "docsToken", "description": "Project MCP token", "password": true }
  ],
  "servers": {
    "myDocs": {
      "type": "http",
      "url": "https://<app-host>/api/mcp/<projectId>/mcp",
      "headers": { "Authorization": "Bearer ${input:docsToken}" }
    }
  }
}
```

Supply the real owner-issued credential when prompted. A redacted placeholder will not work. An OAuth registration prompt indicates a different authentication flow; check the installed URL, configuration and deployed domain. Verify tools/list and a search request after connecting. Secure inputs are specific to the supported VS Code client format.

See the [official configuration reference](https://code.visualstudio.com/docs/agents/reference/mcp-configuration).
