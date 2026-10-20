---
layout: default
title: "Quality and search"
---

# Quality and search

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Separate the measurements

1. Crawl quality: observed extraction and content checks.
2. Coverage: saved pages relative to discovered URLs within the chosen scope.
3. Search relevance: ordering of sections for a query.
4. MCP health: real authenticated endpoint checks.

No single confidence percentage can establish all four. Current AI scores/defaults in services/ai/understanding.ts are legacy estimates, not validated measurements.

## Initial quality report

Report saved/attempted pages, empty/error pages, duplicates, truncations, heading/code-fence checks, source URL validity, indexing success and crawl budget exhaustion. Label coverage as coverage of discovered pages, never of an unknown entire website. Treat syntax checks as indicators; they cannot prove code examples were extracted perfectly. Do not invent an aggregate score before its rubric is implemented and calibrated.

## Retrieval

Reuse heading-aware chunks, breadcrumbs and source provenance. Protect fenced code from arbitrary splitting. Rank useful exact identifiers and section headings alongside body matches. Inspect actual scoring implementation before labeling it BM25/BM25+; an ad hoc weighted matcher is not automatically BM25.

Search returns relevant snippets and source URLs. The agent can fetch a full page as needed. Optional ask_documentation answers use retrieved evidence and cite it; missing evidence should be disclosed. A citation or score never guarantees factual correctness.

## Evaluation

Maintain representative queries for exact symbols, setup, authentication, webhooks and missing topics. Compare expected relevant pages with returned results. Separately test valid/invalid/revoked tokens, cross-project isolation and actual client connections. Measure latency and crawl completion by corpus size and site type before making performance claims.
