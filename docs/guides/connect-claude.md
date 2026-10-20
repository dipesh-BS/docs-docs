---
layout: default
title: "Connect Claude"
description: "Connect Claude for the hosted docs4llm release."
category: "Guides"
order: 39
---

# Connect Claude

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Choose a Claude client/version that supports the hosted endpoint and its authentication configuration. Install the project-specific URL and bearer credential through that client's supported remote MCP setup, then verify tool listing and a documentation search.

Do not assume a browser OAuth connector accepts an arbitrary static bearer token. If a compatible bridge is required, document and test its exact version separately; a client bridge does not deploy the docs4llm backend. The release does not promise universal Claude Desktop configuration support without this check.
