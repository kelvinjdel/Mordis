# Mordis — Claude Context File
# Read this at the start of every session in this folder.

## What this is
A DnD campaign world webpage styled as a historical textbook for a friend's
campaign set in Mordis. Single file (index.html), no framework, no backend,
no server. Includes an embedded HTML5 canvas game called "The Gauntlet of Mordis."
Published at: https://kelvinjdel.github.io/Mordis/

## Owner
ECE master's student, electrical engineering professional. C/C++ is primary
language. Building this as a personal project for their DnD group. Not for
commercial distribution. Prefers concise responses, no filler.

## File structure
- index.html  — everything (page + game, ~1700 lines)
- mordis.png  — map image used as hero background and inline
- test/       — scratch draft, NOT committed to git, local only
- CLAUDE.md   — this file

## Page structure (HTML)
Chapters I–V + Appendix, all in index.html:
- Chapter I:   Kelvin & the Founding of Kelvopolis
- Chapter II:  Expansion & Coexistence (Age of Roots)
- Chapter III: The Sun of Lathander (Braburg Valley event)
- Chapter IV:  The Powers of Mordis (4 nations: Moricci, Nakensia, Alems, Eingarden)
- Chapter V:   The Voyagers (4 characters)
- Appendix:    The Gauntlet of Mordis (canvas game)

The Origins section (pre-history theories) was intentionally removed.
"The Divide" was renamed to "the western expanse" throughout.

### The 4 Voyagers (character cards)
- Belnan    — Halfling Ranger, Lunara'a. Roads went dark, missing travelers,
              came home changed. Doesn't speak of his time.
- Galilei   — Elven Warlock, Meselia. Navigator. Sees things in stars since
              crossing. Patron gave him a trail to trace by his own hands.
- Fugoki    — Dwarf Fighter, Mines of Uroy/Tabra'an. Gentle giant, father
              offered him to the crown. Nothing left to prove at home.
- Mark      — Human Monk, Aquenta. Right Hand of the King. Devil took his
              sight, his sister, and the memory of both.

## The Gauntlet of Mordis — canvas game
HTML5 canvas, 820×320px. IIFE-wrapped JS at lines ~728–1690.

### Key constants
```javascript
const HORIZON = 138;
const LANES = [172, 215, 258];
const T_DUSK = 270, T_BOSS = 550;
const BOSS_HP_MAX = 5;
const SHOT_CD = 120;  // 2 seconds at 60fps
```

### State machine
idle → running → boss → victory (or dead at any running/boss point)
Ship has 3 HP. Collisions are ENABLED (not invincible).

### Obstacles (running state)
- albatross    — swooping bird, dodge by changing lane
- cannonball   — charging bull face, horns curve BACKWARD (trailing), speed lines
- theatrical   — dagger with peacock feather bouquet + helix trail of items
- goldfish     — infernal orange cracker fish, spews soul coins (black rings,
                 red interior) and gold coins

### Boss: Captain Tom
Hull panel fills right 1/3 of canvas. 3×3 cannon port grid (9 ports).
Slides off screen right when HP reaches 0. Triggers victory sequence.
Boss preview: small ship silhouette visible in top-right for first 100 frames
of boss state, drifts off to the right.

### Victory sequence timing
- 0–300:   water transitions red→blue, boss slides away
- 300:     instant star inversion (sky stars swap positions)
- 600+:    ship sails toward island
- 620–840: island slides in from right
- 820:     golden arrival flash (Lathander)
- 900:     beach scene fades in (dawn sky, sand, palm tree)
- 960:     4 characters walk onto beach (Fugoki, Mark, Belnan, Galilei)
- 1030:    characters dance
- 1150:    overlay fades in — "for lathandar" / "we stay pogging" / "Space to sail again"

### Particle system
Parts array. Each particle: {x,y,vx,vy,life,maxLife,size,color,gem,ring}
- gem:true  → diamond shape
- ring:true → black outer ring, dark red (#8a0808) inner circle
- default   → filled circle

### Git
Remote: https://github.com/kelvinjdel/Mordis (public, GitHub Pages enabled)
Branch: master
Deploy: automatic on push to master
