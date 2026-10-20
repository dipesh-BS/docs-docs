---
layout: default
title: "Hosted MCP preparation"
description: "Hosted MCP preparation for the hosted docs4llm release."
category: "Core Concepts"
order: 12
---

# Hosted MCP preparation

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Docs4llm prepares tools for the shared hosted endpoint /api/mcp/{projectId}/mcp. Tinyfish does not generate or host that endpoint.

The baseline tools are list_documentation_pages, get_documentation_page, search_documentation, get_documentation_overview, read_full_documentation and ask_documentation. The core release reads documentation rather than executing vendor business actions.

Readiness requires actual authenticated endpoint checks. Registry listing is separate. No downloadable standalone Node server or generated deployment bundle is included.
