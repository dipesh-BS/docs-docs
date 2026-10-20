---
layout: default
title: "Hosted service"
description: "Hosted service for the hosted docs4llm release."
category: "Deployment"
order: 22
---

# Hosted service

> Updated 2026-10-20. Target release documentation; verify deployed capabilities before relying on planned features.

The product uses the hosted Next.js application and remote MCP endpoint. Users connect an editor or agent using a project-scoped credential; no per-project server deployment is needed.

GitHub Pages hosts documentation separately. It cannot host login callbacks, conversion workers or MCP APIs. The release does not include standalone Node server deployment or generated server bundles.
