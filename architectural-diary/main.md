# Architectural Diary — Arta (Arta Harta Semesta site)

## Project identity

Static one-page marketing site for Arta Harta Semesta, a Bali-based artist
(illustration, watercolor, digital; children's books, botanical art,
commissions). Built as a Mobirise 5 export and hosted on GitHub Pages at
`https://hsingh23.github.io/Arta/`. No backend, no build pipeline, no runtime
dependencies — everything is static HTML/CSS/JS with vendored libraries.

## Timeline

### 2025-05-07 — `2dd61f4` chore: scaffold Mobirise static site with vendored assets

The repository was seeded in a single commit with the full Mobirise export:

- `index.html` (the entire site: navbar, fullscreen parallax hero, badge
  marquee, events cards, fullscreen image break, "Trusted by" partners,
  gallery, YouTube background-video section, subscribe CTA form, four pricing
  tiers, testimonials carousel, metrics counters, FAQ accordion, social
  follow, contact form, contact info block, footer).
- `project.mobirise`, the builder source project, committed alongside so the
  site can be regenerated.
- `assets/` with all libraries vendored (Bootstrap 5, jarallax, masonry +
  imagesloaded, smooth-scroll, scroll-gallery, ytplayer, vimeoplayer,
  navbar-dropdown, formoid, mbr-switch-arrow, socicon + mobirise icons) and
  20+ images.
- Boilerplate `.gitignore`, `.gitattributes` (LF normalization), MIT LICENSE.

Architecturally this fixed the project's shape permanently: one HTML file, one
builder source, a vendor directory, zero infrastructure.

### 2025-05-07 — `ada7297` feat: link navbar Services to #services and Contact to WhatsApp

First content pass over the template:

- Dropped the placeholder `Work` nav item.
- Services → on-page anchor (`.../Arta/#services`); Contact → WhatsApp deep
  link (`wa.me/6285624112528`), choosing a chat channel over email as the
  primary conversion path.
- Republish regenerated formoid form tokens, cache-bust strings, the
  `project.mobirise` menu/features blocks, and Mobirise's promo footer text —
  demonstrating the export churn that any builder round-trip causes.

### 2026-09-08 — Documentation and history hygiene

- Messages-only history rewrite (trees unchanged): `Initial commit` →
  `chore: scaffold Mobirise static site with vendored assets`; `contact` →
  `feat: link navbar Services to #services and Contact to WhatsApp`. Backup
  branch `backup/pre-docs-20260908` retains the pre-rewrite SHAs locally.
- Added README, AGENTS.md, CHANGELOG, this diary, decision records, and a
  one-shot recreation prompt (`../prompt.md`).

## Open architectural threads

- Contact forms post to the Mobirise form endpoint (`mobirise.eu`) — no
  first-party form handling.
- The `#services` anchor has no matching section id (broken in-page target).
- Placeholder links remain on "View Work", "Menu", and event "Book" buttons;
  testimonials and pricing are template content.
- No analytics, accessibility review, or image optimization (several photos
  are >250 KB).

## Decision records

- [001 — Build with Mobirise and commit the builder project](decisions/001-mobirise-static-site.md)
- [002 — Host on GitHub Pages from repo root](decisions/002-github-pages-deployment.md)
- [003 — WhatsApp as primary contact channel](decisions/003-whatsapp-contact-channel.md)
