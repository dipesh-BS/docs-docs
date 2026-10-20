---
layout: default
title: "Connect agent frameworks"
description: "Connect agent frameworks for the hosted docs4llm release."
category: "Guides"
order: 41
---

# Connect agent frameworks

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Use your framework's MCP client to connect to the hosted project endpoint with its project bearer credential. Discover tools and expose search_documentation to the agent. A local search_docs wrapper may forward query and limit to that tool and return its source-bearing results unchanged.

The backend Tinyfish key is never sent to the agent. This release does not add a public docs4llm SDK or promise an OpenAI-specific integration is already tested. Verify the chosen framework's current remote MCP and header support before publishing an example.
