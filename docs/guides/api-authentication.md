---
layout: default
title: "API authentication"
description: "API authentication for the hosted docs4llm release."
category: "API Reference"
order: 15
---

# API authentication

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Project management uses a signed-in app session and owner authorization. Protected MCP tools use Authorization: Bearer <project-token>.

The existing X-Docs4LLM-Token header is a compatibility path. Query-string tokens are not accepted. The target token lifecycle is owner-only issuance, one-time display, hash-only storage and independent revoke/replace. Existing artifact storage and delivery require migration before claiming this is deployed.
