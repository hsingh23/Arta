# Arta — Arta Harta Semesta, Bali Artist Portfolio Site

A one-page static marketing site for **Arta Harta Semesta**, a Bali-based
artist whose work spans illustration, watercolor, and digital media, with a
focus on children's books, botanical art, and personalized commissions. The
site presents services and event offerings (weddings, corporate events, pet
portraits, art sessions), pricing tiers, testimonials, an FAQ, a gallery, and
contact channels. It is published on GitHub Pages at
<https://hsingh23.github.io/Arta/>.

## Why this exists

The site gives the artist a simple, dependency-free web presence that can be
hosted for free on GitHub Pages. It was built by exporting a
[Mobirise](https://mobirise.com) project, so the entire site is plain HTML/CSS/
JS with vendored libraries — no build step, no server, no tracking beyond what
Mobirise embeds.

## Features

- **Hero** — fullscreen parallax header with the artist's tagline and a "View Work" call to action.
- **Events** — cards for Weddings, Corporate Events, Pet Portraits, and Art Sessions, each with a booking button.
- **Trusted by / partners** strip and a YouTube background video section.
- **Subscribe / transform-your-vision** call-to-action form.
- **Pricing** — four tiers (Basic 29, Standard 49, Premium 99, Ultimate 199 per month).
- **Testimonials** carousel and **stats** counters (500+ artworks sold, 300+ happy clients, 10+ years active).
- **FAQ** accordion (experience, materials, custom requests, turnaround, worldwide shipping).
- **Gallery** — masonry image gallery ("Follow Arta's World") with a scroll gallery.
- **Contact** — WhatsApp deep link in the navbar, a contact form, and contact details (Ubud, Bali; phone; email; open hours).

## Tech stack

| Layer | Choice |
| --- | --- |
| Site generator | Mobirise 5 (`project.mobirise` is the source project) |
| Markup / styling | Single `index.html`, Bootstrap 5, Mobirise theme CSS (`assets/mobirise/css/mbr-additional.css`) |
| Fonts | Google Fonts "Brygada 1918", socicon + Mobirise icon fonts (vendored) |
| JS (all vendored) | Bootstrap bundle, jarallax (parallax), smooth-scroll, scroll-gallery, masonry + imagesloaded, navbar-dropdown, ytplayer (YouTube), vimeoplayer, mbr-switch-arrow, formoid (forms) |
| Hosting | GitHub Pages (static; no build pipeline) |

There is no package manager, no bundler, and no server code.

## Quickstart

```bash
# serve the site locally (any static file server works)
python3 -m http.server 8000
# then open http://localhost:8000
```

To publish changes, commit to `main` and push — GitHub Pages serves the
repository root. The live URL is <https://hsingh23.github.io/Arta/>.

### Editing the site

Two options:

1. **Mobirise app (recommended for structural edits):** open `project.mobirise` in the Mobirise builder, edit, and re-export to this repository. Keep `project.mobirise` in sync with `index.html` — it is the only way to regenerate the page faithfully.
2. **Hand-edit `index.html`:** fine for copy/text tweaks, link changes, and image swaps. Be aware the next Mobirise re-export will overwrite hand edits unless they are also made in the builder.

## Repository structure

```text
.
├── index.html            # the entire site — one page, all sections
├── project.mobirise      # Mobirise builder source project (regenerates index.html)
├── assets/
│   ├── bootstrap/        # Bootstrap 5 CSS + JS bundle
│   ├── mobirise/         # generated mbr-additional.css (site-specific styles)
│   ├── theme/            # Mobirise theme CSS/JS
│   ├── dropdown/         # navbar dropdown behavior
│   ├── formoid/          # form handling (posts to mobirise.eu form endpoint)
│   ├── parallax/         # jarallax parallax
│   ├── smoothscroll/     # smooth scrolling
│   ├── scrollgallery/    # gallery scrolling behavior
│   ├── masonry/          # masonry grid layout
│   ├── imagesloaded/     # image load detection for masonry
│   ├── ytplayer/         # YouTube background video
│   ├── vimeoplayer/      # Vimeo player
│   ├── mbr-switch-arrow/ # toggle arrow icon behavior
│   ├── socicon/          # social icon font
│   ├── web/assets/       # Mobirise icons font
│   └── images/           # site artwork and background photos
├── CHANGELOG.md
├── AGENTS.md             # notes for AI coding agents working in this repo
├── prompt.md             # one-shot prompt to recreate this site from scratch
└── architectural-diary/  # design decisions and build narrative
```

## Environment variables

None. This is a pure static site with no runtime configuration.

## Known limitations (placeholders from the template)

- The contact/subscribe forms post to `https://mobirise.eu/` (Mobirise's form endpoint) — they are not wired to the artist's own backend or inbox.
- Several buttons still point at Mobirise placeholders (`https://mobiri.se`), e.g. "View Work", "Menu", and the event "Book" buttons.
- The navbar `Services` link targets `#services`, but no section carries that id — the anchor does not scroll anywhere.
- Testimonial names and pricing are template placeholder content.

## License

MIT — see [LICENSE](LICENSE). Artwork images are the artist's; do not reuse.
