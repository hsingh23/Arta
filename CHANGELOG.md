# Changelog

All notable changes to this project are documented here, newest first.

> **History rewrite note (2026-09-08):** commit messages were rewritten in a
> messages-only history rewrite (same trees, same file contents, new SHAs).
> Both commits below use post-rewrite SHAs; their original subjects were
> `Initial commit` and `contact`.

## 2025-05-07

### feat: link navbar Services to #services and Contact to WhatsApp
**ada729779ec170a68953db4a9e976a03953bccd6** (`ada7297`, previously `ae333ad`) — Harsh Singh

- Remove the placeholder `Work` nav item from the navbar.
- Point **Services** at the on-page `#services` anchor (`https://hsingh23.github.io/Arta/#services`) and **Contact** at a WhatsApp chat link (`wa.me/6285624112528`).
- Regenerate the hidden formoid form tokens for both contact/subscribe forms on republish.
- Update `project.mobirise` block HTML (menu02/features03) to match the navbar edit, plus a routine cache-bust of `mbr-additional.css` query string and Mobirise promo-footer text changes.

## 2025-05-07

### chore: scaffold Mobirise static site with vendored assets
**2dd61f4758c179c6aaae75549605babac368ccd3** (`2dd61f4`, previously `f4c6af6`) — Harsh Singh

- Add `index.html`: the complete one-page marketing site for Arta Harta Semesta, a Bali-based artist (hero, events, pricing, testimonials, stats, FAQ, gallery, contact).
- Add `project.mobirise`: the Mobirise site-builder source project used to regenerate `index.html`.
- Vendor all front-end assets under `assets/`: Bootstrap 5 (CSS + bundle JS), Mobirise theme CSS/JS, dropdown/navbar script, jarallax parallax, smooth-scroll, scroll-gallery, YouTube/Vimeo players, masonry + imagesloaded, formoid forms, socicon and Mobirise icon fonts, and 20+ artwork/background images.
- Add `.gitignore`, `.gitattributes` (LF normalization), and an MIT `LICENSE` (Copyright 2025 Harsh Singh).
