---
layout: default
title: "Shipping checklist"
---

# Shipping checklist

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

These are acceptance gates, not completed tasks.

## Credentials first

- [ ] Reproduce redacted credential delivery and verify the deployed/editor domain.
- [ ] Add owner-only issue/revoke/replace with hash-only storage and one-time raw return.
- [ ] Remove raw credentials from artifacts/logs/public metadata with a compatibility migration.
- [ ] Test missing, invalid, revoked and other-project tokens.
- [ ] Verify exact client configuration in VS Code and Cursor; test supported Claude connection separately.

## Tinyfish and retrieval

- [ ] Verify provider contract/account capabilities and add the minimal adapter.
- [ ] Persist run IDs and resume bounded background work without duplicate paid jobs.
- [ ] Validate URL/network scope, outputs and per-page errors.
- [ ] Save Markdown with code/tables/provenance and surface partial/empty extraction.
- [ ] Verify heading-aware retrieval and evidence-based quality reporting.
- [ ] Test an actual authenticated MCP handshake, tool listing, page read and search.
- [ ] Keep registry publication outside readiness.

## UI and login

- [ ] Preserve submission through login; auto-resume exactly once.
- [ ] Ship focused light workspace and matching landing input.
- [ ] Persist real progress; reload safely; show actionable failures.
- [ ] Make Connect, Pages and Try a question the completion actions.
- [ ] Verify keyboard, mobile and token-replacement flows.

## Release

- [ ] Run configured static/type/build checks and relevant integration tests.
- [ ] Measure timings before publishing performance claims.
- [ ] Update STATUS.md to match verified behavior.
- [ ] Build and check GitHub Pages links after the owner configures publishing.
- [ ] Verify public docs contain no credentials or private project data.

No standalone Node deployment, self-hosted export, new public SDK or automatic registry release is part of these gates. The owner controls publishing and all repository operations.
