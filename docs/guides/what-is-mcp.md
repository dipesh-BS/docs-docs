---
layout: default
title: "What is MCP?"
description: "What is MCP? for the hosted docs4llm release."
category: "Getting Started"
order: 5
---

# What is MCP?

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Model Context Protocol lets an AI client discover and call external tools. Docs4llm exposes tools such as search_documentation and get_documentation_page over a hosted endpoint.

An editor sends a search request, receives relevant sections and source URLs, and uses that context to answer or write code. MCP is the connection standard; it does not itself crawl docs, refresh them or guarantee correctness.
