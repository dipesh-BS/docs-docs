---
layout: default
title: "How it works"
description: "How it works for the hosted docs4llm release."
category: "Getting Started"
order: 6
---

# How it works

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

URL -> login if needed -> durable conversion job -> Tinyfish discovery/extraction -> validated Markdown -> heading-aware index -> hosted MCP checks -> connection token -> editor/agent queries.

The existing application and database remain. Detailed stages are represented by saved logs and existing project statuses. No separate process is deployed for each project. Closing or refreshing the page must not lose submitted work. See [Crawling](crawling.md) and [MCP generation](mcp-generation.md).
