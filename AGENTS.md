# AGENTS.md — working notes for AI coding agents in this repository

## What this repo is

A single-page, Mobirise-generated static marketing site for Arta Harta Semesta
(a Bali artist), published to GitHub Pages at
`https://hsingh23.github.io/Arta/`. There is **no build system, no package
manager, no server code, and no tests**. Everything ships as-is from the repo
root.

## Commands

```bash
# serve locally
python3 -m http.server 8000          # then open http://localhost:8000

# git hygiene
git status --porcelain
git log --oneline --decorate -10
git diff                            # review before committing

# inspect history (messages were rewritten 2026-09-08; SHAs before that live on backup branch)
git show <sha>
```

There is nothing to lint, build, or test. The verification loop is: edit →
serve locally → eyeball the page in a browser → commit.

## Architecture map

- `index.html` — **the whole product**. One page composed of Mobirise `<section>`
  blocks, each with a generated id such as `menu-5-uKtmzEn0Qa`. Section order:
  menu/navbar → hero → features gallery → events → fullscreen image →
  partners ("Trusted by") → gallery → YouTube background video → CTA form →
  pricing → testimonials → metrics → FAQ → social/follow → contact form →
  contact info → footer.
- `project.mobirise` — JSON-ish Mobirise builder project. It is the
  *source of truth for regeneration*: edit in the Mobirise desktop app and
  re-export to update `index.html` + `assets/`.
- `assets/` — vendored, minified libraries (Bootstrap 5, jarallax, masonry,
  imagesloaded, smooth-scroll, scroll-gallery, ytplayer, vimeoplayer,
  navbar-dropdown, formoid, mbr-switch-arrow) plus fonts (Google-hosted
  "Brygada 1918", local socicon / mobirise-icons2) and all images.
  **Treat `assets/` as vendor code — do not hand-edit minified files.**

## Conventions

- Commits follow Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:` …),
  imperative subject ≤72 chars, body explaining what and why.
- Content/copy changes: edit `index.html` text nodes (and mirror in the
  Mobirise app before the next export, or your edit will be lost).
- Structural changes: make them in the Mobirise app via `project.mobirise`,
  then export; never hand-restructure section markup.
- Never commit secrets. Note that Mobirise forms embed an *encrypted email
  token* (`data-form-email` hidden inputs) — these are form-handler artifacts,
  not plaintext secrets, but do not tamper with them outside the builder.

## Gotchas

1. **Hand edits are disposable.** Regenerating from `project.mobirise`
   overwrites `index.html`, `assets/mobirise/css/mbr-additional.css`, and can
   churn cache-bust query strings (`?v=XXXXXX`) plus Mobirise promo-footer
   text. Keep the two in sync.
2. **Broken anchor:** navbar "Services" links to `#services`, but no element
   has that id (real ids look like `features-69-uKtmzEn0Qa`). Fix in the
   Mobirise app, not by hand.
3. **Placeholder links remain:** "View Work", "Menu", and event "Book" buttons
   point to `https://mobiri.se`; forms post to `https://mobirise.eu/`. These
   are template defaults awaiting real destinations.
4. **Personal data in repo:** a WhatsApp number (`wa.me/6285624112528`),
   phone, and email are intentionally public marketing contact channels — fine
   to keep in docs/code, but never add anything private.
5. **History was rewritten on 2026-09-08** (messages-only; trees unchanged).
   Pre-rewrite SHAs survive on local branch `backup/pre-docs-20260908`; do not
   push that branch.

## Verifying changes

- `git status --porcelain` should show only intended files.
- Serve locally and click through: navbar links, WhatsApp link, gallery
  layout (masonry), parallax hero, FAQ accordion, video section autoplay.
- If you touched `index.html`, diff-check that section ids and `assets/...`
  references still resolve (open the console in the browser and look for 404s).
- GitHub Pages serves `main` of this repo — after push, verify the live URL.

## Pointers

- `README.md` — human-facing overview, stack, quickstart, limitations.
- `CHANGELOG.md` — every commit, newest first.
- `architectural-diary/` — decision records (static-site choice, GitHub Pages,
  WhatsApp contact channel) and the build narrative.
- `prompt.md` — a one-shot prompt that recreates this site from scratch.
