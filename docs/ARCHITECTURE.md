---
layout: default
title: "Architecture"
---

# Architecture

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Product boundary

Docs4llm turns documentation into a hosted, searchable knowledge source for AI agents. Tinyfish gathers pages; docs4llm validates, stores, indexes and exposes them. Agents use MCP tools to retrieve relevant sections with source URLs.

```text
Landing/workspace URL input
  -> app login if required, preserving submission
  -> POST /api/convert: validate, authorize, create project/job
  -> background pipeline: Tinyfish discovery/extraction
  -> validated pages in Supabase Postgres
  -> heading-aware chunks, search, optional OpenRouter analysis
  -> existing hosted /api/mcp/{projectId}/mcp endpoint
  -> explicit connection-token issuance -> editor or agent
```

## Existing foundations to reuse

- Next.js application and hosted API routes; Vercel is the current application deployment configuration.
- Supabase Postgres and Drizzle for users, projects and content.
- Existing app authentication and project ownership checks.
- Pipeline worker and QStash scheduling infrastructure.
- Documentation retrieval and MCP runtime.

GitHub Pages hosts static documentation only. It cannot run conversion jobs, login callbacks or MCP endpoints. A local Node.js development/build toolchain does not imply a standalone Node deployment product.

## Execution model

Create jobs quickly, persist provider run IDs, then return control to the user. Prefer asynchronous Agent runs with bounded polling/reconciliation through the existing worker. Each worker invocation stays inside platform limits; do not hold a serverless request open for an unbounded crawl. A closed browser tab must not lose a submitted job. Persist stages, page outcomes and errors so progress can be reconstructed.

## Trust boundaries

An app session manages the owner's projects. The server-side Tinyfish key authorizes provider work. A project MCP token grants read access to one project's docs. These credentials are distinct. Treat crawled text as untrusted source content, not instructions to the crawler, backend or answering model.

Validate public HTTP(S) targets, scope returned URLs, prevent private-network access including redirects, and preserve source provenance. Public GitHub Pages content contains no user data or secrets.

## Scope

Ship the website-docs path and read-only documentation tools first. Existing structured-source parsers can remain; they are not a promise of newly tested support. No per-project process deployment is required: projects share the hosted application runtime with authorization on each request.
