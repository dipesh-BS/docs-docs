---
layout: default
title: "Documentation crawling"
description: "Documentation crawling for the hosted docs4llm release."
category: "Core Concepts"
order: 9
---

# Documentation crawling

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

The target ingestion path uses Tinyfish Agent for interactive navigation/discovery and Tinyfish Fetch for Markdown at known URLs. Manifests and sitemaps are discovery hints. Agent extraction handles pages needing interaction.

The existing HTML/Markdown/Jina path has not yet been replaced in the reviewed baseline. Do not assume all source formats or sites have been validated with Tinyfish.

The backend validates URLs and output, stays within the selected host/path, preserves code and tables, deduplicates content and records failed pages. Coverage means saved pages out of discovered in-scope URLs, not a guarantee of full-site coverage. Public-source access is the release focus; authentication-wall support is deferred.
