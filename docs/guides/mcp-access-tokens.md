---
layout: default
title: "Connection tokens"
description: "Connection tokens for the hosted docs4llm release."
category: "Reference"
order: 17
---

# Connection tokens

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

The shipping flow issues read-only project credentials explicitly to the signed-in owner. Return raw values once, store hashes, and support replacing or revoking access without crawling again.

General project responses stay redacted. Existing user/marketplace tokens are a distinct legacy feature and must not be confused with project credentials. Until migration is complete, verify actual delivery and access behavior rather than assuming a shown placeholder is valid.
