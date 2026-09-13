---
name: reference-photoreal-flagship-method
description: "How to hit award-site (igloo.inc-tier) quality for King's premium web builds: use REAL photoreal assets, not hand-coded 3D primitives. The proven recipe + the headless-WebGL + Vercel-protection gotchas. Proof: NIVA live at kd-niva-ice.vercel.app."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-replica-flagships-2026-06-08
---

# Photoreal Flagship Method (2026-06-08) · how to actually hit "PS6" web quality

## The core lesson (this cost a whole session)
Hand-coding a 3D object from Three.js **primitives** (a hemisphere + wireframe) looks cheap, King called it "PS2 vs PS6". You cannot light/tune your way to award-site quality from primitives. To match a site like **igloo.inc** you need **real assets**:

1. **Generated photoreal RENDER as a parallax hero (THE WINNER, robust):**
   - `python C:\Users\Dell\.claude\tools\kie_generate.py image "<photoreal prompt>" assets/hero.png 16:9` (Nano Banana via KIE) → prints `RESULT_URL=`.
   - Use it full-bleed as a fixed background `<img>`, add CSS/JS **scroll-scale + pointer parallax + grain + vignette**, fade the corner UI out on scroll. No WebGL = renders accurately, no headless guessing, looks photoreal because the asset IS photoreal.
   - **Proof: NIVA**, `Documents\Website Builder\replicas\niva\` → **kd-niva-ice.vercel.app**. Photoreal igloo in a foggy mountain valley + minimal corner UI (brand TL, manifesto TR, scroll-to-discover + sound toggle BL). King approved this as the right tier.
   - Next 10% = real camera MOTION: feed the still to Seedance (`kie_generate.py video`) → slow fly-in → scrub frames on scroll (the Nate Herk method, [[skill-seedance-animated-websites]]).
2. **Real 3D MODEL alternative (for interactive/spinnable):** Meshy text-to-3D (`tools\meshy_generate.py`, [[skill-3d-web-builder]]) + an HDRI environment in Three.js. Heavier; use when the object must rotate live.

## The boundary we hold (King kept pushing for an exact 1:1 clone)
Recreate the **design, layout, motion, feel and quality** of a reference site, but always as **King's OWN brand, with original copy and our own/generated assets.** Do NOT reproduce a source company's logo, brand name, verbatim copy, or proprietary 3D assets/code (that's theirs and can't go in King's portfolio or be sold anyway). "Call it fan art / we're just testing" does not change this. The look carries the value; the brand is his. (Firecrawl can't shortcut it either, a WebGL site's look lives in its model/textures/shaders, not the scrapeable HTML.)

## Gotchas (both bit hard this session)
- **Headless Playwright/swiftshader MISRENDERS real-time WebGL**, it flipped the igloo dome pure-black then blown-white between runs. You cannot judge 3D-shader quality from a headless screenshot. → For real-time WebGL, King must view on his real GPU. The photoreal-image approach (above) screenshots accurately, so prefer it.
- **New Vercel projects ship with Deployment Protection ON** → public URL returns **401**. Disable it: `curl -X PATCH "https://api.vercel.com/v9/projects/<projectId>?teamId=team_mdY7lCt81eu9f702b6X7ttxW" -H "Authorization: Bearer $VERCEL_TOKEN" -d '{"ssoProtection": null}'` (token in `.env.master`; projectId in the folder's `.vercel/project.json`). Then alias to a clean `kd-*.vercel.app`.

## The replica venture (King's "aim-high" targets) · COMPLETE 2026-06-08
King sends premium reference sites; we rebuild each as an original flagship (his brand, changed/own subject, photoreal). His 4 refs: **igloo.inc · aircenter.space · shader.se · artprize "Art Here"**. All 4 now built (each its own brand/world), live + QA'd headless (image/canvas render accurately):
- ✅ **NIVA** (igloo) = kd-niva-ice.vercel.app, now WITH MOTION (scroll-scrub, see below).
- ✅ **ATRIA** (← aircenter) = kd-atria.vercel.app, light-mode white architectural "premium workspace": photoreal white sculptural hero + giant kinetic letters spread across.
- ✅ **PRISMA** (← shader.se) = kd-prisma.vercel.app, dark iridescent liquid-chrome studio; doubles as a studio reel (rows link to real RELAY/VendorIQ/NIVA).
- ✅ **FORMA** (← Art Here) = kd-forma.vercel.app, cream luxury exhibition: filigree-sphere render, elegant Cormorant serif.
- ⚠️ **MAGMA** (volcano, real-time Three.js) = kd-magma-volcano.vercel.app, REJECTED (too low-fi). Lesson above.
- Builds: `Documents\Website Builder\replicas\<slug>\`. Assets batch: `replicas\_gen_assets.py`. QA capture: `replicas\_qa.py`. Study shots: `replicas\_study\`.
- All clone the NIVA `index.html` pattern (loader → fixed photoreal bg → fading corner UI → spacer → reveal panels → CTA), only palette/type/hero/copy change.

## NIVA motion = the "final 10%" recipe (real camera move, proven)
1. Seedance video from the ALREADY-HOSTED still (no re-gen): `kie_generate.py video "<slow push-in...>" hero.mp4 https://kd-niva-ice.vercel.app/assets/hero.png 8 1080p 16:9` → cinematic fly-in.
2. Extract frames: `ffmpeg -i hero.mp4 -vf "fps=12,scale=1280:-2" -q:v 5 assets/frames/f_%03d.jpg` (~97 frames, ~3MB, light).
3. In `index.html`, replace the fixed `<img>` with a fixed `<canvas>`; preload the frames; in the rAF loop map smoothed scroll progress → frame index and `drawImage` (cover-fit ×1.08 + pointer parallax). Keep `<img>` as no-JS fallback. This frame-scrub is mobile-safe and renders in headless (unlike real-time WebGL).

## Deploy gotcha learned 2026-06-08 (on top of the protection-PATCH one)
A NEW Vercel project's first non-interactive deploy needs **`--scope king-david-s-projects2`** (team) or it fails `missing_scope` / `action_required`. So: `vercel deploy --prod --yes --scope king-david-s-projects2 --token=$VERCEL_TOKEN`. Already-linked projects (e.g. niva) don't need it. Team/org id = `team_mdY7lCt81eu9f702b6X7ttxW`; account = kdagbidiloveschrist / king-david-s-projects2.

Related: [[feedback-top-tier-design-standard]] · [[feedback-each-3d-world-truly-unique]] · [[skill-seedance-animated-websites]] · [[knowledge-demo-library]].
