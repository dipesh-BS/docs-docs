---
layout: default
title: "Project API"
description: "Project API for the hosted docs4llm release."
category: "API Reference"
order: 18
---

# Project API

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

POST /api/convert starts a conversion; GET /api/projects/{id} returns owner-visible redacted status and logs. POST /api/projects/{id}/retry is the existing retry route.

Existing statuses: pending, crawling, analyzing, generating, ready, error. Partial failures should be stored as warnings rather than inventing a new database status without a migration. New token issuance and richer progress APIs are planned, not yet frozen contracts.
