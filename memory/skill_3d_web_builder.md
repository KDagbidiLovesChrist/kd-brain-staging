---
name: skill-3d-web-builder
description: Premium immersive 3D website builder, real pipeline (text-to-3D model + HDR studio lighting + Three.js scroll-through-3D world). Built + approved by King 2026-06-03. Reusable + sellable as a high-ticket web service; portfolio demo = levi-pro-v2.vercel.app.
metadata: 
  node_type: memory
  type: project
  originSessionId: 2eca88c8-7c08-4047-a50e-d740fe22ddee
---

# 3D Web Builder skill (LIVE, King-approved 2026-06-03)

A genuine **immersive 3D website** capability, the camera FLIES THROUGH a 3D world as you scroll (Dora.run / Awwwards style), not a flat page with effects. King pushed hard for this over a long session; final build approved ("its good"). **Sell as a high-ticket premium-3D-website service; add to the web gig portfolio as a demo.**

## The live demo (portfolio-ready)
- **https://levi-pro-v2.vercel.app**, "The Levi System" concept (physique/aesthetics 1:1 coaching). Bespoke obsidian statue hero + real HDR studio lighting + glowing tunnel/stations + smooth scroll. Source: `Documents\Website Builder\proofs\levi-pro-v2\` (and the lineage `levi-world-v1..v5`, `levi-world-pro`, `levi-pro-v1`).

## The pipeline (how to reproduce / the real skill)
1. **Bespoke 3D model** via Meshy text-to-3D API → `tools\meshy_generate.py "<prompt>" "<out.glb>"` (key `MESHY_API_KEY` in `.env.master`, free tier). Generated the hero statue from a prompt; download the GLB.
2. **Real HDR studio lighting (IBL)**, download a CC0 HDR from Poly Haven (`dl.polyhaven.org/file/ph-assets/HDRIs/hdr/1k/<name>_1k.hdr`), load via Three.js `RGBELoader` → `PMREMGenerator.fromEquirectangular` → `scene.environment`. THIS is the biggest "studio render" quality lever (realistic reflections). Procedural `RoomEnvironment` is the fallback.
3. **Three.js r128 world**: full-screen fixed canvas; Lenis smooth scroll → scroll progress drives a camera flying through a deep tunnel past glowing stations; particles, helix; GLTFLoader for the model with premium `MeshPhysicalMaterial` (obsidian: near-black, clearcoat 1.0, low roughness, envMapIntensity ~2.2) + emerald/gold spotlights + soft contact shadow.
4. **Post-processing**: UnrealBloom + cinematic colour-grade. (See lessons, DOF was removed.)
5. **"Watch reference" tool**: `tools\gemini_watch_ui.py --youtube/--file` (Gemini 2.5-flash) reverse-engineers premium UI/UX from any video into a build spec. Studies saved in `knowledge\video_studies\`.
6. **Build method King likes**: relay of agents (each improves the previous) + a consensus pick at the end.

## Hard-won lessons (do these)
- **Depth-of-field / heavy full-screen blur = BAD here**: it both LAGS and makes the background look soft/low-quality. King wanted "smooth + 4K-sharp + pop" → remove DOF, cut particle counts, tighten bloom, add an adaptive FPS guard. Sharp + smooth beats over-processed.
- **Scroll bug fix**: for a Lenis window-scroll fly-through, the DOCUMENT must be the scroller. `#scroll-space` ~700vh; `html,body` must have NO `height:100%`; body `overflow-y` must stay `visible` (setting `overflow-x:hidden` on BODY silently makes the body an internal scroller and Lenis then can't scroll → "can't scroll"). Put `overflow-x:hidden` on `html` only.
- **"3D website" to a client means the PAGE moves in 3D space** (camera flythrough), not a 3D model in a box. Mis-read this several times before landing it.
- **Quality leap = bespoke generated asset + real HDR IBL**, not more code tricks. Grey stock mannequin + procedural light = "webgl demo"; bespoke statue + HDR = "studio render".
- **Vercel gotcha**: copied folders carry a `.vercel` project link → deploys to the wrong project. Delete `.vercel` before deploying a copied folder, then alias to a clean public name. Verify the clean alias returns real HTML (not the Vercel "Authentication Required" SSO page).
- **Tool-augmentation mindset** (King's): wire a free key/API around any capability wall, Gemini = video eyes, Meshy = bespoke 3D, Poly Haven = lighting. [[feedback-tool-augmentation]]

## Uniqueness rule (do NOT reskin for portfolio/client work)
Reusing this engine with only new colours + hero = a RESKIN, which King rejects for portfolio/client pieces ("each website will have unique", 2026-06-03). Reuse only the PRIMITIVES (renderer, HDR IBL, bloom, Lenis, FPS guard, overlay/scroll system). The WORLD must be new each time: its own 3D concept + camera motion. Proven distinct examples: Levi = fly-through tunnel · VEYRA = 360° gallery orbit around the gem · FLUX = self-assembling data-network. Also: overlay text must stay readable (scrim + shadow + ≥0.85 opacity). See [[feedback-each-3d-world-truly-unique]].

## Honest quality ceiling
Lands a genuine ~8.5/9 (sharp, smooth, premium, sellable, beats most freelancers). A literal Dora/Awwwards 10 = a studio's weeks of art direction (baked AO/normal maps, SSAO, hand-tuned scenes). Good enough to sell and to send to the LMS lead.
