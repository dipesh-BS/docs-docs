---
layout: default
title: "Frequently asked questions"
description: "Frequently asked questions for the hosted docs4llm release."
category: "Reference"
order: 30
---

# Frequently asked questions

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

## Is this already migrated to Tinyfish?

The reviewed baseline still uses the older crawler. These docs describe the agreed migration and clearly identify required work.

## Why use MCP instead of pasting docs?

It gives agents reusable search/page-reading tools across a saved corpus. A short pasted page can still be sufficient for a one-off question.

## Are answers guaranteed correct or always current?

No. Inspect sources and coverage. Content is a snapshot until refreshed; automatic refresh is deferred.

## Do I deploy a Node server?

No. Use the hosted endpoint. Local development dependencies are separate.

## Will Privy fix MCP authentication?

No. It is an optional website login provider, separate from project tokens and editor OAuth.

## Does it always finish in 60 seconds?

No timing guarantee is made; measure representative sites before advertising targets.
