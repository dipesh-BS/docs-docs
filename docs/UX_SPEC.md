---
layout: default
title: "User experience"
---

# User experience

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Landing

Lead with: Give your AI the docs it needs. Provide a documentation URL field, Create MCP action, a few examples and a short explanation of searchable, cited context. Do not promise universal timing, complete crawling, zero hallucinations or automatic freshness.

## Login and resume

Allow input before sign-in. On Create MCP, preserve URL/options and open login when needed. Resume once after verified login; cancellation preserves input. Validate everything server-side. Use the existing login initially; Privy is optional and requires an identity mapping/migration decision. A provider swap does not implement editor MCP OAuth.

## Workspace

Use the supplied Tinyfish screenshot as visual inspiration: light canvas, subtle borders, generous spacing, restrained accent and focused input. Keep docs4llm branding. Sidebar: New MCP, My servers, Settings. Main input: URL; optional focus instructions; collapsed scope/page-budget options. Users do not need to configure JSON Schema, provider products or credentials.

## Processing

Show the current stage, elapsed time, saved-page count and safe warnings from persisted job state. Show denominators only when known. Refresh resumes the same job. Include cancel only after backend/provider cancellation works. Avoid fake percentages, fabricated page events and an unexplained spinner.

## Result

Primary actions: Connect editor, Browse pages, Try a question. Show endpoint health separately from crawl quality. Provide client-specific configurations, explicit token issuance and replace/revoke controls. Never let redacted placeholders appear as usable credentials. Show partial failures with affected URLs and retry. Empty extraction is an error, not ready.

## Secondary surfaces

Keep existing CLI/marketplace features compatible while removing them from the main conversion path. Registry listing is opt-in later. No generated Node server download, deployment wizard, mandatory chat conversation or exposed schema editor.

## Accessibility

Keyboard-operable input/modal/actions, visible focus, readable contrast, mobile layout, announced progress and actionable inline errors are required.
