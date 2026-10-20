---
layout: default
title: "Architecture and workflow"
description: "Architecture and workflow for the hosted docs4llm release."
category: "Reference"
order: 21
---

# Architecture and workflow

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Conversion writes extracted content and project state to Supabase Postgres. Agent queries read the saved project corpus through the hosted MCP runtime after authorization.

The target flow preserves submission through login, uses durable Tinyfish jobs, indexes accepted pages and checks the real endpoint before readiness. App login, crawling and MCP tokens are separate concerns. The static GitHub Pages docs site hosts none of these backend operations.
