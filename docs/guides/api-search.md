---
layout: default
title: "Search tools"
description: "Search tools for the hosted docs4llm release."
category: "API Reference"
order: 20
---

# Search tools

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Search is exposed through MCP tools; no separate REST /search or /ask route is promised.

Call search_documentation with query and optional limit. Results should include source sections, breadcrumbs and citation URLs. Call get_documentation_page for fuller context, or optional ask_documentation for an evidence-grounded answer.

Use a framework wrapper named search_docs if useful; it forwards to the existing MCP tool. Missing evidence should be reported rather than invented.
