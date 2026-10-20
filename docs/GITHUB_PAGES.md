---
layout: default
title: "Publish documentation on GitHub Pages"
---

# Publish documentation on GitHub Pages

> Shipping specification, updated 2026-10-20. This describes the agreed target; it is not a claim that the migration is deployed. See [implementation status](STATUS.md).

## Source

This docs/ directory is a standalone Jekyll source. It contains index.md, technical specifications, user guides, a small layout and _config.yml. Publishing documentation does not deploy the application or its APIs.

If the repository root is docs4llm/, choose that repository's /docs folder as the Pages source. If the repository root is the enclosing docs4llm_tinyfish directory, GitHub's branch-source selector cannot choose /docs4llm/docs: copy the contents of docs4llm/docs into a dedicated docs repository root or your publishing repository's /docs folder. Alternatively configure a custom Pages build with docs4llm/docs as its source. No repository operations or publishing are performed by this documentation update.

## Owner setup

1. Set _config.yml url to the public site origin and baseurl to /REPOSITORY for a project site, or an empty string for a root/custom-domain site.
2. In repository Settings -> Pages, select the desired branch and /docs (or root for a dedicated docs repository). Jekyll is the intended branch build.
3. After publication, open the home page, a technical page and a nested guide. Check navigation, styling and links under the repository base path.
4. Configure a custom domain only if desired; no domain is assumed here.

Use the documented publishing-source options: [GitHub Pages source configuration](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Build behavior

Pages use YAML front matter and the bundled default layout. jekyll-relative-links rewrites local Markdown links to rendered routes. Layout links use relative_url so the configured baseurl is respected. Keep app-host examples as placeholders until the production origin is confirmed. Do not copy .env files, app code, database dumps or historical build outputs into the publishing source.

The docs source needs no application environment variables or Node server. A local Jekyll build requires a separate Ruby/Jekyll environment; source/link validation is not a substitute for a successful Pages build.
