# AURUM Gallery — project memory

Project-specific context and preferences. Read at session start; update as decisions land.

## Status
- 2026-06-23 — Pass #2 shipped: hero copy rewrite, brighter filled CTA, accessible mobile menu, and all four sub-pages (Visit, Exhibitions, Artists, Membership) built from shared `style.css`/`script.js`.

## Decisions (settled — don't relitigate)
- **Keep the Hermes skeleton.** This is a design-copy exercise; fidelity to the reference layout is the assignment, not an accident.
- **Real public-domain art, no placeholders.** Empty gradient boxes read as "AI slop" on a gallery specifically. Met Open Access (CC0), key-free, hotlinked.
- **Hero headline:** "The work is the only light." (chosen over "A living collection, hung in the dark." — that read morbid + contradicted the gold-as-light system).
- **Primary CTA stays filled** (bright gold `#E0B85A`), not ghost — "Become a Member" is the page's primary action. Ghost = secondary CTAs only.
- **Build one real flow before templating four.** Visit page is the proven flow; others inherit its primitives.

## Preferences observed (how Ziwen works on this project)
- Convenes `/council` before/after build passes; wants the *tension* surfaced, not averaged.
- Wants to **compare and eyeball output** — build the variants, then let Ziwen judge.
- Reference-first, constraints up front, refine one element at a time, branch by duplicating.
- Opus for the design work. Token-efficient: keep responses skimmable.
- Copyright-aware: public-sector / public-domain art only.

## Gotchas
- `#visit` was circular (pointed at the hero cards container). Sub-page links must resolve to real pages, never same-page jumps that dead-end.
- Don't flood gold as fill or drop the dimmed-image filter — either breaks the one-gallery thread.
- AURUM is fictional; keep the "design study / fictional gallery" honesty in the footer fineprint.

## Open / next
- Real map embed vs. styled map plate on Visit (currently a styled plate — fictional address).
- Membership "gift a membership" option flagged as on-brand (Giftnote-adjacent) — included as a secondary tier action.
