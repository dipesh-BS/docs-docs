---
layout: default
title: "Knowledge processing"
description: "Knowledge processing for the hosted docs4llm release."
category: "Core Concepts"
order: 10
---

# Knowledge processing

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Accepted Markdown is normalized, deduplicated with locally computed hashes and split into heading-aware sections. Each section retains its parent headings, page title and source URL. Protect fenced code from arbitrary splitting.

Preserve full accepted page content for retrieval. Record truncation explicitly if a limit is reached. OpenRouter analysis can summarize docs; inferred API/workflow details are secondary to a usable searchable corpus. Content hashes support change detection but do not schedule refresh by themselves.
