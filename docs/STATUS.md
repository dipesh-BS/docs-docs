---
layout: default
title: "Implementation status"
---

# Implementation status

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

Updated 2026-10-20 after a read-only source review. No live credentials, deployed services, or editor connection were tested in that review.

| Area | Source baseline | Shipping requirement |
| --- | --- | --- |
| Website ingestion | Existing Markdown/HTML crawler with Jina fallback | Tinyfish Agent discovery and Tinyfish Fetch extraction |
| Tinyfish dependency | No SDK dependency or Tinyfish adapter found | Add one verified integration and validate output |
| Conversion pipeline | Existing crawl, analysis, generation, persistence | Reuse orchestration; make provider runs resumable |
| Search and MCP | Existing heading-aware retrieval and JSON-RPC route | Verify actual ranking and protocol compatibility end to end |
| Credentials | Pipeline creates token/hash; artifacts also contain plaintext; project reads redact credentials | Explicit owner-only issuance, hash-only token storage, revoke/replace independently of crawl |
| Editor issue | Screenshot shows OAuth registration failure on doc2mcp.site | Check installed URL, deployed domain and credential delivery separately |
| App login | Supabase Auth plus app session cookie | Preserve submitted URL through login; Privy remains optional |
| UI | Existing landing, conversion and dashboard views | Simplify around create, progress, pages and connect |
| Registry | Publish call currently occurs before final ready update | Remove publication from readiness path; explicit opt-in later |
| Documentation | Revised source and GitHub Pages configuration | Owner publishes; site build not yet verified |

## Known credential-delivery defect

`app/api/projects/[id]/route.ts` and `app/convert/[id]/page.tsx` redact project data, while the result UI reads the token/config from those artifacts. Redacted placeholders can reach connection controls. This is evidence of a delivery defect, not proof that random token generation failed. Fix issuance and ownership checks without removing redaction from general project responses.

## Deferred

Standalone Node server deployment, generated server-code downloads, self-hosted MCP export, a new public TypeScript SDK, custom domains, marketplace expansion, automatic registry publishing, billing changes and MCP OAuth authorization-server implementation are outside this release.

Historical PDFs, slide decks and inspection outputs describe earlier proposals. They are presentation artifacts, not current specifications. This documentation and the approved scope supersede their timing, deployment, tool-count and roadmap claims.
