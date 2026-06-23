# AURUM Gallery

A small static site for **AURUM**, a fictional contemporary art gallery.

It began as a design study — a faithful re-skin of the [Hermes Agent](https://hermes-agent.nousresearch.com/) landing layout (Nous Research) — re-themed from a dark technical product page into a gallery identity: warm gold (`#C9A24B`, CTA `#E0B85A`) on near-black (`#0B0B0C`), Cormorant Garamond display serif with Space Mono catalog labels. It has since grown real sub-pages.

## Pages

| File | Purpose |
|---|---|
| `index.html` | Home — hero, ways to visit, now showing, six numbered sections |
| `visit.html` | Hours, admission, location, tours — the real "plan a visit" flow |
| `exhibitions.html` | Now showing, upcoming, and past exhibitions |
| `artists.html` | Collection artists, a curatorial statement, residencies |
| `membership.html` | Three tiers, gift-a-membership, join |

Shared `style.css` and `script.js` are linked by every page — one design system, no per-page styles.

## Built with

- Plain HTML/CSS/JS, no framework, no build step. Open any `*.html` in a browser.
- Accessible mobile nav (`script.js`), `prefers-reduced-motion` honored, descriptive `alt` on every artwork.
- Real public-domain artworks (CC0), courtesy of [The Metropolitan Museum of Art Open Access](https://www.metmuseum.org/hubs/open-access).

## Project conventions

See `CLAUDE.md` for the locked design system and accessibility guardrails, and `memory.md` for decisions and preferences.

---

Sandbox demo only. AURUM is fictional; addresses, prices, and exhibition dates are illustrative. All artworks are in the public domain.
