---
name: project-galaxy-hub
description: "Galaxy Hub, King's premium site, now LIVE at kingdavidagbidi.com (apex+www aliased to kd-hub-v2). Immersive cosmic fly-through: golden-cosmos hero (King at laptop, the cosmic_right render he LIKED) → photoreal Seedance galaxy → planet-to-planet journey w/ 8 real Nano-Banana 3D planets, each flies in from its own direction → gig-world galleries. Euros everywhere, interactive cursor-tilt cards, cinematic loader, ambient toggle. Smooth phone+laptop. Shipped 2026-06-04."
metadata: 
  node_type: memory
  type: project
  originSessionId: bc30d689-9b4e-4d56-a5d9-c9797ba65071
---

# Galaxy Hub · kingdavidagbidi.com (LIVE)

**Live:** https://kingdavidagbidi.com (apex + www) · **Preview/source of truth:** https://kd-hub-v2.vercel.app · **Folder:** `C:\Users\Dell\Documents\Website Builder\kd-hub-v2\`
**Status (2026-06-04):** SHIPPED + polished + King-approved on phone AND laptop.

## The experience (top → bottom)
1. **Hero** = golden cosmos, **King typing at a laptop on the RIGHT, headline on the LEFT**, the `cosmic_right` render he LIKED (not exactly his face, but the one he chose). Seamless boomerang loop `hero.mp4`.
2. **Photoreal galaxy journey** = a real Hubble-style **Seedance** fly-through (`journey-bg.mp4`) that plays as you scroll (play/pause on scroll, capped playbackRate).
3. **Planet-to-planet journey** = 8 gig **planets** (real **Nano Banana** 3D renders, `planets\*.png`), each **flies in from its own direction in space** (`ax/ay` anchors in `journey.js`) → grows to centre → you "fly in" → the **gig-world card** opens (real demo gallery + links). Only ~1-2 planets render at once (culled).
4. Pricing / how-we-work / contact, all **euros**, with **cursor 3D tilt + follow-glow** on the cards (`.kd-glow`, desktop).
5. **Loader** (KD ring + shimmer, fades on load) + **ambient space-sound toggle** (♪, OFF by default).

## How it's built (key pieces)
- `journey.js`, the scroll engine: `progress()`, `frame()` drives per-planet approach/travel (`ax/ay` sweep) + scale/opacity + card open + deep-field parallax + video play/pause. **Backup: `journey-backup.js`** (pre-planet-to-planet engine, for instant revert).
- `app.js`, Lenis smooth-scroll, nav, count-up, dust canvas, **interactive cursor-tilt+glow on cards**, **loader fade**, **ambient toggle**, hero autoplay.
- `style.css`, `.cosmos`, hero override, `.journey-*`, `.gig-planet` (image clipped to a circle via `border-radius`, NO mask, masks lagged laptops), `.world-card`, `.kd-glow`, `.kd-loader`, `.amb-toggle`.
- Planets: `planets\*.png` (cropped to fill; originals in `planets\full\`). Generated via `tools\kie_generate.py` (Nano Banana). Galaxy still via Nano Banana → animated via Seedance.

## PERF lessons (smooth on phone + laptop)
- **Cull far planets** (`visibility:hidden` + `willChange:auto` when beyond the window), only 1-2 render.
- **No `mask-image` on planets** (GPU-heavy, lagged laptops) → `border-radius` clip on cropped images.
- **No continuous planet animations** (atmoDrift removed); cap video `playbackRate` (~1.6).

## HERO · the likeness saga (important)
King wants the hero to be EXACTLY him. AI (Nano Banana edit + Seedance) **redraws → alters his face** → rejected. Matting his REAL clip (`best.mov`) via **rembg** keeps his real face but reads as a cutout + boomerang-reverse looked "ew" + the layout flip annoyed him → **he chose to revert to the original golden-cosmos `cosmic_right` hero.** Real-matte version PARKED: `hero-real.mp4`, `cosmic_real.png`, `_rh_out\` frames, `tools\build_real_hero.py`. See [[feedback-hero-likeness-and-perf]].

## SHIP / domain
kingdavidagbidi.com (team **king-david-s-projects2**, Third-Party/Namecheap DNS) aliased apex+www → kd-hub-v2 prod deployment. **Caveat: future deploys need re-alias** (`vercel alias set <new-prod-url> kingdavidagbidi.com` + www).

## NEXT
**Video ads** (King will show references → build) → roll the galaxy template + cursor-tilt feel to his **other sites** → **SEND leads**. Reusable template = `journey.js` + `journey-bg.mp4` + planet PNGs + `.cosmos/.world/.gig-planet` CSS + `.kd-glow` module.

## Money/spend
€0 earned. ~$4-5 KIE this session. Hub = the premium front door, now live; leads still unsent.
