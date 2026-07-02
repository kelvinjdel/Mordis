---
project: Mordis
last_touched: 2026-07-02
---

# Mordis — STATUS

## In-flight (2026-07-02) — markdown-driven Persons register
The entire "Persons of Present Account" register in `index.html` now renders **live from
`data/registry.md`** via a small client-side parser injected near `</body>` (mounts into
`<div class="npc-register" id="npc-register" data-src="data/registry.md">`). Preserves the
exact `npc-entry` markup, `.npc-crew/.npc-ally/.npc-shadow` colors, and expand/collapse
behavior (renderer binds its own toggles). Must be served over HTTP (fetch).
- Content edits folded in: **David** removed (Second Vessel), **Yertle** removed
  (Companions), **Kermit → crew** (gold, matches Jocasta), **Paul + Tony** added to the
  First Vessel. Existing wording carried over verbatim.
- **Live**: pushed to master → GitHub Pages published. Paul is a Claude draft; Tony reads
  "Account not yet written."

## Next concrete step
Kelvin finalizes `data/registry.md` — rewrite Paul in his voice, **write Tony**, optionally
add the four Voyagers / more First Vessel crew (a comment marks where). Edit md → push →
Pages redeploys.

## Blockers
- None.

## Recent decisions (most recent first)
- 2026-07-02: full markdown-drive of the NPC register (one `registry.md`), not a hardcoded/rendered mix
- 2026-07-02: David + Yertle removed; Kermit border matched to Jocasta (crew); Paul + Tony added to First Vessel
