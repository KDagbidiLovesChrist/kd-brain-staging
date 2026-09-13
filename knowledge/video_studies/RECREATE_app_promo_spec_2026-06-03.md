# RECREATE SPEC · minimal line-driven app promo (for the r/DesignJobs lead, 2026-06-03)
Synthesised from 3 Gemini motion studies of the poster's own inspo videos. Full studies saved alongside this file (`*_MOTION_*.md`).

## The lead
Design student, final-year project, needs a **30-60s minimal app-promo video** (After Effects style). Their app "has a lot of LINES instead of dots" and "similar colours" to ref #3. They'll share a brandbook + app screens later. They want to see a small sample first.

## The 3 references
- **#3 `8qOZLgRU_Go`, "TOTALLY the vibe" (lead ref):** Lumar/Deepcrawl rebrand. Dark blue `#13122D` ↔ light purple `#F5F0FF`, vibrant cyan `#00F0FF` ("Ultra Blue"), purples `#A375DF`/`#3D0B7A`. Thin 1-2px cyan lines DRAW ON (Trim Paths), curve/branch, form logo outlines. Snappy, cut to ~120-130bpm electronic, whooshes + clicks + shimmers. Geometric sans, kinetic type slide/mask-up. iPhone + laptop mockups for showcase.
- **#1 `LcGPI2tV2yY`, "lines not dots":** Apple "Intention" film. Minimal grey `#E8E8E8`/dark `#1A1A1A`, text `#333`. Lines draw on to connect dots into geometric shapes (square/octagon) + dot-to-line burst networks. Slow, deliberate, piano ~80-100bpm, gentle eases.
- **#2 `bQnSSVESxl4`, "movements":** Breakout Blocks. Purple `#6A25FF` gradient, type-on text, dashed connecting lines (marching-ants), floating app-screen cards sliding in with ease-out overshoot, upbeat ~120-130bpm.

## THE SYNTHESISED STYLE TO DELIVER
Minimal, **line-driven**, kinetic-type app promo. Cyan-on-dark + light-purple palette. Lines are the hero (the client said lines, not dots). Motion cut to the beat. Floating minimal app-screen mockups. Geometric sans typography.

### Palette
- BG dark `#13122D` · BG light `#F5F0FF` · accent cyan `#00F0FF` · purple `#6A25FF` / `#A375DF` · text white `#FFFFFF` (on dark) / `#222` (on light).

### Typography
- Geometric sans (Space Grotesk / Montserrat / Poppins). Tight tracking. Light/Regular for body, Semibold/Bold for emphasis.

### The line technique (most important)
- Thin 2px cyan strokes, animate `stroke-dashoffset` (SVG) / Trim Paths (AE) from hidden to drawn, 0.5-0.9s, fast ease. Lines sweep in curves, branch, and connect UI elements / form shapes. Small endpoint accents OK but keep LINES dominant.

### Motion + pacing
- Snappy ease-out with slight overshoot (cubic-bezier(.34,1.56,.64,1)) for type/UI; smooth ease for lines/bg.
- Typical move 0.3-0.5s. Cut/land key events on the beat (~0.45s grid at ~130bpm).
- Scene transitions: bg colour shift (dark↔light), circular wipe, slide-through. Whoosh + click SFX on every reveal.

### App-screen showcase
- Minimal phone/laptop frame (rounded-rect outline, soft shadow). UI elements animate in individually; thin cyan lines connect them to show flow.

### Structure for a 30-60s cut
1. 0-3s hook: dark bg, two cyan lines draw on + sweep to centre, app name types on.
2. 3-12s: 3-4 one-line value props, each with a line accent drawing on + a UI element.
3. 12-40s: feature showcase, phone mockup, UI elements + connecting lines, cut to beat.
4. 40-55s: "everything connected", line network linking all features.
5. 55-60s: logo + tagline + CTA, lines resolve into the logo.

## DELIVERY PLAN
- **Now:** a short (~12-15s) LIVE animated style sample in this exact look (generic placeholder app) = the bespoke "I nailed your vibe" proof, on top of King's existing video-samples.vercel.app.
- **On a yes / brandbook shared:** build the full 30-60s cut with THEIR screens + brand, render to mp4 (Remotion or headed-capture), deliver.
- Tooling: a new Remotion "LineKinetic" style OR self-contained HTML/SVG + headed-Playwright capture. Music: licence-free 125bpm electronic; SFX whoosh/click.
