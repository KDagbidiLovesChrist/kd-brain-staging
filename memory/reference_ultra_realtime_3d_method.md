---
name: reference-ultra-realtime-3d-method
description: "How to get igloo.inc / Noomo-tier graphics quality from REAL-TIME 3D by stacking AI photoreal imaging + cinematic post on top. Proven on kd-site-v3 / hero-ultra (King's Gold Dust KD hero)."
metadata: 
  node_type: memory
  type: reference
  originSessionId: e7f03826-5818-437b-983c-47c672a31639
---

King's question (2026-06-09): can we combine real-time 3D with AI realistic imaging (Seedance/Nano Banana)
to get igloo.inc-tier quality? **Yes.** igloo.inc IS real-time 3D, the "ultra" look comes from stacking
three things on top of the 3D. This is the recipe (proven on `hero-ultra` + `kd-site-v3`).

## The 3 quality levers (stack all three)
1. **AI photoreal environment**, generate an equirectangular studio HDRI with `tools\gemini_image.py`
   (prompt: "equirectangular 360 HDRI of a dark luxury studio, golden softbox + rim lights, photoreal").
   Load it: `tex.mapping = THREE.EquirectangularReflectionMapping; scene.environment = pmrem.fromEquirectangular(tex).texture`.
   Now metal/glass reflects a BELIEVABLE world → instantly photoreal. Also gen a cinematic **backdrop**
   image and put it on a far plane behind the 3D.
2. **Cinematic post-processing** (EffectComposer): `UnrealBloomPass` + **`BokehPass` (depth-of-field)** +
   a custom **grain/vignette/chromatic-aberration** ShaderPass. DOF + grain = the "expensive film" texture.
3. **Refined particles**, for a dust/letterform, use **`MeshSurfaceSampler`** on the (thin) TextGeometry to
   sample MANY fine points evenly across the surface (NOT raw vertices = chunky). Small `size`, additive,
   gold gradient, gentle flow. Plateau the assemble curve so it HOLDS the formed shape:
   `a = clamp(1.55*(1 - abs((t*0.13 %1)*2 - 1)), 0, 1)`.

## Stack (modern Three)
r160 ESM via import-map: `three` + `three/addons/`. Imports: FontLoader, TextGeometry, MeshSurfaceSampler,
EffectComposer, RenderPass, UnrealBloomPass, BokehPass, ShaderPass, RoomEnvironment (instant env fallback
before the AI HDRI loads). `MeshPhysicalMaterial{transmission:1,...}` gives real glass in r160 (refracts the
scene/headline behind it), r128 cannot.

## Pro tips / gotchas
- "Object too big / unprofessional" fix = pull the camera back (smaller object framed with space) + smaller,
  lighter headline + a clean sans (Inter/Helvetica/Grotesk). Add a live font-switcher to let King pick.
- For readable CONTENT over a bright AI backdrop, fade in a radial dark **#scrim** only on those beats.
- Headless WebGL won't render → QA with **headed Playwright** (`launch(headless=False)`), screenshot each
  scroll stage, and **Read the PNG** to actually see it. Verify 0 console errors + no horizontal overflow,
  desktop AND mobile.
- New Vercel projects: the raw `*-hash.vercel.app` URL can be 401 (deployment protection) but the clean
  `<name>.vercel.app` alias is public, give King the alias.
- See cost tiers for image/video sourcing: [[reference-api-cost-tiers]]. Build originals, not clones.
