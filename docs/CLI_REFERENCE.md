---
layout: default
title: "Existing CLI compatibility"
---

# Existing CLI compatibility

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

The CLI remains an optional client of the hosted application. Users do not deploy an MCP server or run a local server process to connect. This release prioritizes the web journey and agent retrieval; CLI behavior must be rechecked after credential changes.

Commands currently declared in cli/src/index.ts include:

```text
docs4llm login
docs4llm <docs-url>
docs4llm list
docs4llm install <projectId>
docs4llm chat [target]
docs4llm whoami
docs4llm logout
docs4llm token create
docs4llm token list
docs4llm marketplace <projectId>
```

Do not advertise `docs4llm add`, unsupported editor flags, JSON flags or a new SDK as shipped features. Marketplace commands are legacy compatibility, not release priorities. The CLI login token is distinct from a project MCP token; it must never be pasted into an editor as a substitute.

Use local package scripts to build/test the CLI when changing its contract. Do not publish a new package as part of documentation preparation.
