# AURUM Gallery — project instructions

A multi-page static site for a **fictional** contemporary art gallery, "AURUM". Started as a design-copy study (a re-skin of the [Hermes Agent](https://hermes-agent.nousresearch.com/) landing layout) and is growing real sub-pages. Sandbox only — fictional gallery, public-domain art.

## What this is
- Static HTML/CSS/JS, no build step, no framework. Open any `*.html` in a browser.
- Pages: `index.html` (home), `visit.html`, `exhibitions.html`, `artists.html`, `membership.html`.
- Shared `style.css` + `script.js` — **all pages link these**. Do not re-inline styles per page.

## Locked design system (do not relitigate)
- **Palette:** bg `#0B0B0C`, raise `#121113`, warm white `#EDEAE3`, muted `#A39E92`, gold `#C9A24B`, **bright gold `#E0B85A`** (CTA fill only), hairline `rgba(201,162,75,.18)`.
- **Type:** Cormorant Garamond (serif, headings) + Space Mono (labels/numerals). Google Fonts, `display=swap`, system fallbacks.
- **Gold = light, never paint.** Gold for the radial glow, hairlines, italic accents, links, and the *one* primary button per view. Never gold panels/backgrounds.
- **Brand motif that must carry to every page:** the gold em-dash bracketing the `AURUM` wordmark; catalog numerals (`№ 01…`); dimmed-image filter on artworks (`saturate(.92) brightness(.92)`).
- **Voice:** curatorial wall-label — short, present-tense, restrained. Never feature-benefit/product copy. Never contradict the actual offer (hours, free Thursdays).

## Components (reuse, don't reinvent)
`.card` (3-up row), `.feature` + `.frame` (numbered block with matted/captioned art), `.featured` (now-showing band), `.tiers` (membership), `.page-hero` (sub-page header). Build new pages from these.

## Accessibility guardrails (every page)
- Primary CTA must be the **filled bright-gold** button; secondary CTAs use `.btn--ghost`.
- Mobile nav is a real `<button aria-expanded aria-controls>` toggled by `script.js` — never a checkbox-hack.
- One `<h1>` per page, sane heading order, descriptive `alt` on every artwork, underlined inline links (never colour-alone), visible `:focus-visible`, `prefers-reduced-motion` honored.

## Ring-fence
Fictional gallery, public-domain (CC0) art from the Met Open Access only. No production data. Nothing ships to a real surface without senior review.

## Working notes
- Project context + preferences live in `memory.md` (this folder). Read it at session start.
- Full project brief + council decisions: `~/Documents/zz-vault/01-projects/AURUM Gallery — Hermes Re-skin.md`.
- Git: personal account `zzwzzwzz` / `ziwenzhou.zz@gmail.com`. Remote: `git@github.com:zzwzzwzz/AURUM-Gallery.git`.
