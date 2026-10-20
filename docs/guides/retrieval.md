---
layout: default
title: "Search and retrieval"
description: "Search and retrieval for the hosted docs4llm release."
category: "Core Concepts"
order: 11
---

# Search and retrieval

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Agents call search_documentation with query and optional limit. The service returns ranked documentation sections with breadcrumbs and source URLs; get_documentation_page reads the full saved page when needed.

An agent framework can wrap this call as search_docs. That convenience name is not a separate deployed REST endpoint. Reuse the existing retrieval implementation and verify exact-symbol and natural-language queries before making ranking or latency claims.

Optional ask_documentation synthesizes an answer from retrieved evidence. Citations support verification; they do not guarantee correctness. No vector database or new SDK is required for the initial release.
