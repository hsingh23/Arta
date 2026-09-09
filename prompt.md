# One-shot recreation prompt — Arta (Arta Harta Semesta site)

Use the prompt below to recreate this project from scratch with an AI coding
agent. It reproduces the site's goal, stack, structure, content, and design
decisions. The acceptance criteria at the end define "done".

---

## Prompt

Build a **single-page static marketing website** for "Arta Harta Semesta", a
Bali-based visual artist. The page must be one self-contained `index.html`
plus an `assets/` directory of vendored libraries and images — **no build
step, no package manager, no server code**. It will be hosted on GitHub Pages
at `https://<user>.github.io/Arta/`.

### Goal

Give the artist a fast, free, zero-maintenance web presence that showcases
services, pricing, social proof, and — above all — drives visitors to a
WhatsApp chat.

### Brand & content

- **Identity:** Arta Harta Semesta, Bali artist. Vibrant, story-rich artwork
  across illustration, watercolor, and digital media; specializing in
  children's books, botanical art, and personalized commissions.
- **Font:** Google Fonts "Brygada 1918" (400/700), loaded asynchronously with
  `<link rel="preload" ... onload>` + `<noscript>` fallback.
- **Contact info to display:** phone +62 81234567890, email
  arta@hartasemesta.com, address Ubud, Bali; hours Mon–Fri 9am–5pm.

### Page sections, in order

1. **Navbar (sticky):** brand "Arta"; links **Services** (in-page anchor) and
   **Contact** (WhatsApp deep link `https://wa.me/6285624112528`); a primary
   "Menu" button.
2. **Hero:** fullscreen parallax background; H1 "Arta"; tagline "Bali artist
   crafting vibrant, story-rich art."; primary button "View Work".
3. **Badge marquee:** scrolling strip of "Best offers / Free delivery /
   Perfect design / Comfort / Support 24/7 / Vibes".
4. **Events:** four cards, each with image, title, date, blurb, "Book" button:
   - Weddings — May 15, 2025 — "Capture your special moments with a custom painting."
   - Corporate Events — June 1, 2025 — "Create lasting memories with a unique artistic experience."
   - Pet Portraits — June 10, 2025 — "Celebrate your furry friends with a personalized portrait."
   - Art Sessions — July 4, 2025 — "Join a creative workshop and unleash your inner artist."
5. **Fullscreen image break** (parallax background).
6. **"Trusted by"** partners strip.
7. **Gallery:** masonry image grid ("Follow Arta's World"), 20 photos of
   artwork, using masonry + imagesloaded.
8. **Video section:** fullscreen YouTube background (embed
   `https://www.youtube.com/embed/wjQq0nSGS28`, autoplay, muted, looped,
   controls hidden).
9. **Subscribe CTA:** "Transform Your Vision" with an email form.
10. **Pricing:** four cards — Basic 29, Standard 49, Premium 99, Ultimate 199
    (all "//month"), each with a one-line pitch and "Select Plan".
11. **Testimonials:** carousel; six quotes with avatar names (Robert Downey,
    Scarlett Johansson, Chris Evans, Gwyneth Paltrow, Mark Ruffalo, Jeremy
    Renner) — placeholder names are fine.
12. **Stats counters:** 500+ Artwork sold, 300+ Happy clients, 10+ Years active.
13. **FAQ accordion:** team experience, materials used, custom requests,
    turnaround time, worldwide shipping.
14. **Contact form:** "Get In Touch" (name/email/message) + **Contact Info**
    block with the details above.
15. **Footer:** "© 2025 Arta Harta Semesta. All rights reserved."

### Stack & vendored libraries (all local, no CDN)

- Bootstrap 5 (CSS + `bootstrap.bundle.min.js`).
- Parallax: jarallax (CSS + JS). Smooth scrolling: smooth-scroll.
- Gallery: masonry + imagesloaded + scroll-gallery JS.
- Media: ytplayer (YouTube background), vimeoplayer.
- Navbar dropdown JS; toggle-arrow JS.
- Forms: formoid (`formoid.min.js`), forms `POST` to `https://mobirise.eu/`
  with an encrypted-email hidden input (placeholder handler — acceptable).
- Icons: socicon + mobirise-icons2 fonts, vendored with `@font-face`.
- Custom styles in `assets/mobirise/css/mbr-additional.css` + theme CSS/JS.
- Optional but recommended: keep a `project.mobirise` builder source file so
  the page can be regenerated in the Mobirise app.

### Phased build order

1. **Phase 1 — Skeleton:** `index.html` with `<head>` (title "Arta Harta
   Semesta: Bali Artist - Illustrations, Murals, and Art Services", meta
   description summarizing the artist), font loading, and empty section
   markup with ids.
2. **Phase 2 — Vendor assets:** lay out `assets/` (bootstrap, parallax,
   smoothscroll, scrollgallery, masonry, imagesloaded, ytplayer, vimeoplayer,
   dropdown, mbr-switch-arrow, formoid, socicon, web/assets icons, theme,
   mobirise) and wire all `<link>`/`<script>` tags at the end of `<body>`.
3. **Phase 3 — Sections:** build navbar, hero, marquee, events, image break,
   partners, gallery, video, CTA, pricing, testimonials, stats, FAQ, contact
   form/info, footer with the copy above.
4. **Phase 4 — Behavior:** dropdown menu, smooth-scroll anchors, parallax
   init, masonry layout, testimonial carousel, FAQ accordion, counters.
5. **Phase 5 — Polish & ship:** placeholder images (art-themed stock photos),
   favicon, MIT LICENSE, `.gitignore`, `.gitattributes` (LF normalization);
   push to a GitHub repo and enable Pages on the root of `main`.

### Design decisions to preserve

- **WhatsApp-first contact:** the navbar Contact link is the wa.me deep link;
  forms are secondary.
- **Rooted hosting path:** the site lives at `/Arta/` on Pages, so in-page
  links from full URLs must include the `/Arta/` prefix (bare `#fragment`
  hrefs work only if the anchor id exists).
- **No runtime dependencies:** every library is vendored and minified; do not
  introduce npm or a bundler.
- **Keep the builder source** (`project.mobirise`) in the repo next to the
  export.

### Data model

None — static content only. The only "data" is the artwork images in
`assets/images/` and the hardcoded copy in `index.html`. Forms are handled by
an external endpoint and require no local storage.

### Acceptance criteria

1. `python3 -m http.server` in the repo root serves the complete site at
   `/` with no console errors and no 404s for local assets.
2. All 15 sections render in order with the specified copy and behave:
   navbar dropdown, smooth in-page scrolling, parallax hero and image break,
   masonry gallery, background video autoplaying muted, working FAQ accordion,
   animated counters.
3. Navbar **Contact** opens `https://wa.me/6285624112528`; **Services**
   targets an anchor id that actually exists in the page.
4. The site is a single `index.html` + `assets/` (+ optional
   `project.mobirise`); there are no build scripts, no node_modules, and no
   runtime dependencies.
5. Repo contains MIT LICENSE, `.gitignore`, `.gitattributes`; pushing `main`
   publishes via GitHub Pages at `https://<user>.github.io/Arta/`.
6. Page title and meta description match the brand identity above.
