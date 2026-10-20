---
layout: default
title: "Security"
description: "Security for the hosted docs4llm release."
category: "Enterprise"
order: 27
---

# Security

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Use trusted source URLs and keep credentials out of shared configs, public registry metadata, query strings and logs. App sessions, provider keys and MCP credentials have separate scopes.

Target controls include owner authorization, hashed project tokens, revoke/replace, network-scope validation, bounded crawling and treating fetched text as untrusted content. Known credential-storage/delivery gaps must be fixed and tested before claiming those controls are complete. Report vulnerabilities privately to docs4llm@gmail.com.
