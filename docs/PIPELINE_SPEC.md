---
layout: default
title: "Conversion pipeline"
---

# Conversion pipeline

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## 1. Submit

Keep the URL and optional focus instructions through login. Validate and authorize on the server, check the configured usage budget, and prevent duplicate jobs on repeated submit. Return a project identifier promptly. Stage labels must reflect stored state rather than a simulated percentage.

## 2. Discover and extract

Use manifests/sitemaps as discovery hints, Tinyfish Agent for interactive navigation, and Tinyfish Fetch for clean Markdown at known URLs. Scope discovery to approved hosts/paths; prioritize getting started, auth and API guides. Use a configurable starting budget (for example 40 pages), not a claim of complete site coverage. Provider capability and budget must be verified before enabling it.

Save run IDs and page results. Bound attempts, wall-clock duration, page count and output size. A timeout is not successful completion. Retry only failed pages where possible and report partial coverage.

## 3. Normalize and index

Validate result shapes, resolve/validate URLs, reject empty or error pages, strip boilerplate, preserve code fences and tables, and hash normalized content for deduplication. Store full accepted content; if a size limit truncates it, record that limitation. Use heading-aware sections with breadcrumbs and source links. Verify actual ranking with representative code identifiers and natural-language questions before describing it as BM25.

OpenRouter may generate summaries and cited Q&A. Endpoint/auth/workflow inference is secondary and must not gate access to otherwise usable documents. Hash comparison avoids reindexing unchanged content; it does not by itself implement scheduled refresh.

## 4. Prepare and verify MCP

Register the project's documentation tools in the shared hosted runtime. Run actual authenticated endpoint checks: handshake, tools/list, page retrieval and search. Keep protocol/authentication failures separate from content quality warnings. Proposed token issuance must support this check without storing plaintext in artifacts or logs.

## 5. Connect

Mark ready only after the required checks pass. The owner issues a connection token and receives a client-specific configuration. Partial page failures appear as ready with warnings, using warning metadata alongside the existing status enum. Registry publication is outside the readiness path.

## State compatibility

Reuse persisted statuses: pending -> crawling -> analyzing -> generating -> ready, or error. More detailed labels belong in job metadata/logs; do not document additional database enum values as implemented. Persist retry attempts and safe error messages. A resumed job must not duplicate paid runs or silently invalidate existing tokens.

## Acceptance

A signed-out user submits once, logs in, resumes automatically, refreshes during processing, receives a usable corpus, issues a valid token and obtains cited results from an editor. Also verify duplicate submit, provider failure, partial results, empty results, wrong token, cross-project access, revoke/replace, and refresh after token issuance. Measure timings; no universal under-60-second promise.
