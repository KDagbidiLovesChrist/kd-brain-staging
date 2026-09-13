---
name: reference-whole-page-cinematic-engine
description: "The 'whole page is the cinematic journey' build (Elypt-grade): footage scrubs the ENTIRE scroll as a fixed backdrop with content acts over it + interactivity. Plus the perf killers and the frame-0 black-hero bug that MUST be avoided. Proof: kd-isola/marea/aether/ascent."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-cinematic-whole-page-2026-06-08
---

# Whole-Page Cinematic Engine (2026-06-08)

King's standing bar for the cinematic sites = **Elypt's "30 hero sections" videos**: the AI footage must carry the WHOLE page, not just a hero band on top of a flat text page. This is the v2 engine that delivers it. Builds on [[skill-seedance-animated-websites]] + [[feedback-no-handcoded-3d-cinematic-method]] + [[reference-photoreal-flagship-method]].

## The standard (build once, theme per site)
- **Footage = persistent backdrop.** `<canvas>` is `position:fixed; inset:0; z-index:0` and the frame index maps to **global document scroll** (`scrollY / (scrollHeight-innerHeight)`), so the clip plays through the entire page. Content sits z-index:10 over it; each "act" has its own scrim gradient so light text reads over busy footage (all sites use light text + per-palette dark scrims, Elypt-style).
- **Elypt furniture:** fixed top nav (brand · links · **Book a call** pill), headline **bottom-left** (punchy serif), small-caps kicker, **two pill CTAs**, "scroll to explore" cue + gold line, corner micro-label, side chapter ticks, thin gold scroll-progress bar.
- **5 acts over the footage:** hero → statement → service cards (hover tilt+glow) → kinetic serif line (drifts with scroll) → CTA. Then a solid footer.
- **Interactivity:** Lenis smooth scroll · custom cursor dot+ring (desktop only) · footage pointer-parallax · scroll-driven **push-in zoom** (the "dive into the scene" feel) · reveal-on-scroll · clickable ticks → `lenis.scrollTo`.

## ⚠️ PERFORMANCE KILLERS · never do these over a moving canvas
A site that's laggy reads as cheap/broken no matter how pretty. The big costs (King called it "laggy on phone and laptop"):
1. **`backdrop-filter: blur()` on cards over a repainting canvas**, the browser re-blurs every frame. REMOVED → solid translucent card bg `rgba(var(--card),.72)`.
2. **A `mix-blend-mode` grain/overlay layer over the canvas**, blend recomputed every repaint. REMOVED.
3. **dpr=2 full-viewport redraw every frame.** Cap dpr ≈ `min(touch?1.4:1.6, devicePixelRatio)`.
4. **Redrawing when nothing changed.** Dirty-check: only `drawImage` when frame index / zoom / parallax actually moved. When idle = **0 redraws** (verified). 

## 🔴 THE FRAME-0 BLACK-HERO BUG (cost a whole debug loop · avoid forever)
Symptom: the hero is **black until you scroll** (worse on a phone / slow connection). Cause: the dirty-check marked frame 0 as "drawn" even when its image hadn't loaded yet → once it loaded, nothing was "dirty" so it never repainted. TWO guards are required together:
1. Only mark drawn **after** a real paint: `if(im&&im.naturalWidth){ drawCover(im,zoom); lastIdx=idx; ... }` (don't set lastIdx when the image isn't ready).
2. **Force a repaint whenever ANY frame loads:** in the image `onload`, set `lastIdx=-1`. Bulletproof against load-timing races.
This black-hero bug likely contributed to the whole set feeling "mid" on his phone. Always verify the hero paints (below).

## Mobile "too zoomed in" fix
A 16:9 clip on a tall phone cover-crops hard. Fixes: drop the baked-in overscan (start cover at exactly 1.0), and use a gentle scroll **push-in** (`zoom = 1 + sprog*(touch?0.12:0.22)`) so it starts wide and dives in (not over-zoomed at rest). Hide the bottom corner label < 560px so it doesn't collide with the scroll cue.

## QA technique (headless can't judge *feel*, but can catch black/broken)
- Sample canvas pixels: `ctx.getImageData(...)` average brightness > 0 ⇒ hero actually painted (immune to screenshot caching). 0 = black hero bug. Live values that passed: ISOLA 118, MARÉA 110, ASCENT 140, AETHER 57 (dark by design).
- Check `scrollWidth>innerWidth` (overflow), footage advances (brightness changes across scroll), `.reveal.in` count, console errors. Lenis eases jump-scrolls, so reveal counts mid-jump read low, not a bug. Final aesthetic gate is ALWAYS King on his real GPU/phone.

## Deploy gotchas
- All 4 are linked Vercel projects (scope `king-david-s-projects2`). `vercel deploy --prod --yes --scope ... --token=$VERCEL_TOKEN` then `vercel alias set <prod-url> kd-<slug>.vercel.app`.
- A **batched alias loop can silently fail** for one site (its success line just doesn't print) → the alias keeps pointing at the OLD deploy. After deploying, **verify the live HTML actually changed** (`curl <url> | grep -c '<marker>'`), don't trust the batch.
- Seedance clips often **fade in from black**, but extracting frames from a bright source still gives a bright f_001, the black hero was the JS bug, not the footage.

## The live sites (sources in `Documents\Website Builder\replicas\`)
- **ISOLA** (island, turquoise) = kd-isola.vercel.app · `replicas\portfolio\island\` (dramatic descend-into-villa clip via `replicas\portfolio\_island_dramatic.py`)
- **MARÉA** (villa, warm gold) = kd-marea.vercel.app · `replicas\marea\` (231 frames, 2 clips)
- **AETHER** (space, cosmic blue) = kd-aether.vercel.app · `replicas\portfolio\space\`
- **ASCENT** (architecture, golden steel) = kd-ascent.vercel.app · `replicas\portfolio\architecture\`
- **HALCYON** (immersive 3D city, cyan/amber on indigo-night) = kd-halcyon.vercel.app · `replicas\halcyon\` (2026-06-09). Original fictional smart-city / property-development brand ("A city built for the next hundred years"). Nano Banana blue-hour metropolis still → Seedance 8s aerial DESCENT (wide skyline → glide forward+down past a foreground tower into the river/bridges) → 193 frames (fps=24) → MARÉA engine, rebranded (Fraunces serif + Sora, cyan #54e6d0 + amber #f0b878 accents, NOT King's black+gold). 6 acts incl. a stats/"by the numbers" act. KIE spend ~$1.33. QA PASSED desktop+mobile (hero paints 77/66, footage advances 77→45 on scroll, 0 site console errors, no overflow). This is the reusable "immersive 3D city" template.
- All 4 are on **kingdavidagbidi.com** "Cinematic Flagships" grid (Veyra card removed for them). Thumbs = a hero frame copied to `kd-site-v2\assets\flagships\<slug>.jpg`.

## Next level (offered, not built): stitch a 2nd clip per site for a longer continuous "all the way inside" journey (e.g. ISOLA: descend over beach → glide inside a villa), MARÉA-style. Costs a bit more KIE credit.
