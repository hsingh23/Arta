# ADR 001 — Build with Mobirise and commit the builder project

- **Date:** 2025-05-07 (commit `2dd61f4`)
- **Status:** Accepted

## Context

The artist needed a polished one-page web presence quickly, with no interest
in maintaining a JS framework, build pipeline, or hosting infrastructure. The
site is pure marketing content: sections, images, a form, contact details.

## Decision

Build the site in the Mobirise 5 visual builder and commit **both** its
outputs (`index.html`, `assets/`) and its source project (`project.mobirise`)
to the repository.

## Consequences

**Positive**

- Zero build/runtime toolchain; the repo is deployable as-is by any static host.
- Visual editing keeps the barrier low for non-developer maintenance.
- `project.mobirise` in git means the site can be regenerated after any breakage.

**Negative**

- Hand edits to `index.html` are lost on the next builder export unless mirrored there.
- Every republish churns unrelated bytes (cache-bust strings, promo footer,
  form tokens), making diffs noisy.
- Vendor directory is minified and effectively unreviewable; upgrades happen
  only through the builder.
- Section ids are generated (`features-69-uKtmzEn0Qa`), so stable anchors for
  in-page links require deliberate edits.
