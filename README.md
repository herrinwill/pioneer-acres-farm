# Pioneer Acres

A land-to-infrastructure homestead progression game. Claim a raw frontier parcel,
survey it, build the systems that keep you alive — water, food, shelter, energy,
storage, waste — grow into a stable homestead, then lift the whole valley with
community infrastructure.

Everything ships as a **single self-contained `index.html`** (inline CSS + JS, no
build step, no server) plus an `assets/` folder of baked background art and a
numbered PNG sprite pack.

## How to run

- Open `index.html` directly in Chrome, Edge, or any modern browser.
- Append `?autotest=1` (e.g. `index.html?autotest=1`) to self-verify: the game plays
  itself through the full progression and shows a green **AUTOTEST: PASS** box in the
  bottom-left corner.

## How to play

1. **Landing → Intro → Map** — read the three intro cards, then pick a parcel on the frontier map.
2. **Work Land** — click the glowing star to begin, then inspect all 7 survey hotspots to learn the land.
3. **Build the chain** with the left tool rail (Build / Water / Farm / Systems / Energy / People):
   survey → shelter → secure water (well → tank → trough → lay pipe) → plant 8 crops →
   storage → energy (solar/wind → battery → wire) → compost → livestock → greenhouse.
4. **End Day** rolls the weather (Clear, Drought, Storm, Cloudy, Cold Snap, High Wind, Heat Wave).
   Each system mitigates specific weather (tanks vs. drought/heat, battery & wind vs. cloudy,
   greenhouse vs. cold snap, shelter/barn vs. storm).
5. **Homestead Stability** unlocks once every core system plus the greenhouse is in place.
6. **Community Projects** — spend surplus water, energy, and materials into the Community Well,
   Battery Hub, Wind Farm, and Water Tower. Finish all four to reach Level 6, *Pioneer Grid Builder*.

## Architecture

Single IIFE exposed as `window.PioneerAcres`. One `state` object (re-initialised by `reset()`),
screens toggled by `show(id)`, build gating in `canPlace()`, stability in `stable()`, level mapping
in `currentLevel()`, daily simulation in `endDay()`, and community logic in `contribute()`.
`window.PioneerAcres.runAutoTest()` walks the full path to stability and community completion and
sets `document.body.dataset.testResult`.

## Assets

- `assets/bg/` — full-screen baked backgrounds: `landing.png`, `frontier-map.png`, `valley.png`, `raw-acre.png`.
- `assets/pa/NN_category/NN_category_NN.png` — 16 numbered sprite categories (water, animals, people,
  tools, props, hydro, wind, solar, power lines, rural/community buildings, farm systems, logistics,
  roads, community props, industrial utilities).
