---
layout: default
title: "Data model"
---

# Data model

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

`lib/db/schema.ts` and applied SQL migrations are authoritative for existing database columns. This document describes responsibilities and required changes; it does not declare tables that have not been implemented.

## Existing entities

- User and app identity/session integration: project ownership.
- PlatformProject: source, status, crawl data, generated artifacts and logs.
- Page: persisted page-level content where used by the current pipeline.
- PipelineJob / ProjectEvent: work tracking and events.
- McpServer: hosted configuration and tools.
- McpAccessToken: existing user/marketplace access tokens, distinct from project tokens.
- CLI auth/token entities: retained compatibility surface, outside the main web journey.

## Required persistence

Persist provider run IDs, attempt state, discovered/attempted/saved/failed page counts, budget exhaustion and safe warnings so processing can resume. Store canonical URL, title, full accepted Markdown, type, content hash and fetch time for accepted pages. Prefer existing tables/metadata where suitable; introduce migrations only for actual schema changes.

## Project tokens

Current code embeds plaintext project credentials and their hash in artifacts. Replace this with project-scoped token records containing hash, label/identifier, creation time, revocation state and optional last-used time. Raw values are returned once by an owner-only issuance operation. Remove raw tokens and credential-bearing configs from persistent artifacts after a deliberate compatibility migration. Never silently invalidate installed clients during a crawl retry.

## Identity

Keep existing internal user IDs stable. Supabase remains the database. If Privy is selected later, map its verified issuer/subject to the existing user; do not merge accounts solely on an unverified email. Define ownership/row-access controls before moving identity providers.

## Migrations

Review new SQL before applying it. Do not renumber or rewrite applied migration history. Database changes and deployment are owner-controlled release operations; a documentation refresh does not run migrations.
