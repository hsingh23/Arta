# ADR 003 — WhatsApp as primary contact channel

- **Date:** 2025-05-07 (commit `ada7297`)
- **Status:** Accepted

## Context

The template's contact paths were placeholders (a `https://mobiri.se` link
and forms posting to Mobirise's demo endpoint). The audience is largely
tourists and local clients in Bali, where WhatsApp is the dominant messaging
channel.

## Decision

Make the navbar **Contact** item a WhatsApp deep link
(`https://wa.me/6285624112528`), ahead of email or the on-page form, as the
primary conversion path. Keep the email form as a secondary path.

## Consequences

**Positive**

- One tap from mobile opens a chat with the artist — the lowest-friction
  contact path for the target market.
- No backend needed for the primary channel.

**Negative**

- The number is hardcoded in `index.html`; changing it requires an edit (and
  ideally a builder round-trip).
- The on-page forms remain wired to the Mobirise endpoint and can silently
  underperform until replaced or removed.
- wa.me links expose the number to scraping; acceptable here because it is
  public marketing contact data.
