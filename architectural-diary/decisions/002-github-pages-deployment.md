# ADR 002 — Host on GitHub Pages from repo root

- **Date:** 2025-05-07 (evidenced in commit `ada7297`)
- **Status:** Accepted

## Context

The site is fully static and the repository already lives on GitHub
(`hsingh23/Arta`). A hosting choice was needed with no cost and no ops work.

## Decision

Serve the repository root on GitHub Pages at
`https://hsingh23.github.io/Arta/`. Publishing = pushing to `main`; there is
no build step and no `docs/` or `gh-pages` indirection.

## Consequences

**Positive**

- Free, zero-configuration hosting; deploys are just `git push`.
- HTTPS and global CDN come for free.

**Negative**

- The site is rooted under `/Arta/`, so absolute-path assumptions break; the
  nav's Services link therefore uses the full URL
  `https://hsingh23.github.io/Arta/#services` rather than a bare `#services`
  href.
- No server-side capabilities (redirects, form handling, headers) — form
  submission must rely on an external endpoint (currently Mobirise's).
- A custom domain for the artist would require extra Pages configuration
  (not done).
