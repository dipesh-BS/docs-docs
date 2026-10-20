---
layout: default
title: "Keys and tokens"
description: "Keys and tokens for the hosted docs4llm release."
category: "Reference"
order: 16
---

# Keys and tokens

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Keep three credentials separate:

| Credential | Purpose |
| --- | --- |
| App session | Manage your projects |
| Tinyfish API key | Backend crawling; never exposed to editors |
| Project MCP token | Read one project's documentation |

Existing project tokens use d2mcp_; existing user/marketplace and CLI tokens have separate prefixes and scopes. Do not depend on a prefix as proof of authorization. Replace or revoke through the protected connection flow when implemented; no recrawl should be required.
