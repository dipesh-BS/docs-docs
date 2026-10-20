---
layout: default
title: "Access control"
description: "Access control for the hosted docs4llm release."
category: "Enterprise"
order: 26
---

# Access control

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

Project-management requests require the owner app session. A project MCP token grants read access to its saved corpus only. Verify project scope on every protected request.

The shipping target includes owner-only issuance and revoke/replace independent of recrawling. Existing marketplace/user tokens have different access semantics and require explicit regression checks. Do not advertise team roles or enterprise isolation beyond verified controls.
