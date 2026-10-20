---
layout: default
title: "Developer guide"
---

# Developer guide

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Local setup

The application lives in the docs4llm directory. Use the packageManager version declared in package.json (currently pnpm 10.32.1) and a Node version supported by the pinned Next.js release. Node is a local build/development dependency, not a standalone MCP deployment target.

```powershell
pnpm install
pnpm dev
```

Create `.env.local` manually from the variables below; do not assume `.env.example` exists.

| Variable | Purpose |
| --- | --- |
| AUTH_SECRET | App session encryption/signing configuration |
| NEXT_PUBLIC_APP_URL | Canonical hosted application origin; localhost for development |
| POSTGRES_URL | Supabase Postgres connection |
| NEXT_PUBLIC_SUPABASE_URL | Supabase project URL |
| NEXT_PUBLIC_SUPABASE_ANON_KEY | Public client configuration |
| SUPABASE_SERVICE_ROLE_KEY | Server-only privileged operations |
| TINYFISH_API_KEY | Planned Tinyfish adapter, server-only |
| OPENROUTER_API_KEY | Existing analysis and optional cited Q&A |
| QSTASH_TOKEN and signing keys | Background queue and worker verification |
| UPSTASH_REDIS_REST_URL / UPSTASH_REDIS_REST_TOKEN | Optional caching/rate limiting |

Configure enabled sign-in providers in the auth service. Existing auth uses Supabase; Privy is a decision to evaluate, not a required dependency. Registry credentials, payment keys and search-provider keys are not prerequisites for the core release.

## Checks

```powershell
pnpm check
pnpm exec tsc --noEmit --skipLibCheck
pnpm exec next build
$env:PLAYWRIGHT = 'True'
pnpm exec playwright test
```

The package's pnpm build command also invokes database migration code; use it only with the intended environment. Run migrations deliberately after reviewing SQL. Tests requiring Supabase/provider credentials need a configured test environment; do not report unrun live checks as passing.

## Development order

Fix token delivery and ownership, integrate Tinyfish, verify search/MCP, simplify UI/login resume, then align deployment and public docs. See [shipping checklist](SHIPPING_CHECKLIST.md).

## Documentation

The static site source is docs/. App guide content remains in contents/docs for existing routes. Canonical specifications define scope; update both guide surfaces together. See [GitHub Pages setup](GITHUB_PAGES.md).
