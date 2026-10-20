---
layout: default
title: "Agent compatibility"
description: "Agent compatibility for the hosted docs4llm release."
category: "Core Concepts"
order: 13
---

# Agent compatibility

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Target clients are MCP-capable editors and agent frameworks. Validate each advertised client version with actual handshake, tools/list and search calls; protocol labels alone do not establish compatibility.

Connect using the hosted URL and project-scoped bearer token. App login and provider keys are not substitutes. A framework can expose search_documentation through its MCP client as a local search_docs tool. See [MCP setup](mcp-setup.md).
