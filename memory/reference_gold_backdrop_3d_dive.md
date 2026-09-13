---
name: reference-gold-backdrop-3d-dive
description: "kd-site-v3 method: real-time 3D gold particle backdrop behind the untouched KD hero (two-pass composer), the r160 backgroundRotation freeze bug, the 3D dive-into-flagship transition, and the AURA flagship pattern. Built 2026-06-10."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-site-v3-2026-06-10
---

# Gold backdrop + 3D dive (kd-site-v3 method)

How King's hub (`Documents\Website Builder\kd-site-v3\index.html`, Three.js **r160 ESM**) got its
moving gold background, without disturbing the **KD particle hero** (the dust that morphs KD→worlds→hand on scroll).

## ⚠️ THE FREEZE BUG (this is why "it's not moving" · check this first)
- `scene.backgroundRotation` **does NOT exist in three.js r160** (added in r163). Calling
  `scene.backgroundRotation.y = ...` throws `TypeError: Cannot set properties of undefined (setting 'y')`
  **every frame, before `composer.render()`** → the whole scene FREEZES once that line is reached.
- Symptom: renders fine for a split second (before an env image loads / before the throwing line), then
  static; console fills with the same error. **Fix: don't use backgroundRotation on r160.**
- Also: a **flat image** background barely reads as "moving" on King's phone (too subtle) and **iOS Low
  Power Mode throttles requestAnimationFrame** to ~1fps (freezes WebGL). → **Always use real-time 3D
  particles for "living" gold, not a flat picture.**

## Gold particle backdrop behind an ORBITING hero (two-pass composer)
The KD hero camera ORBITS; a fixed gold field must sit behind it. Don't use a 2nd canvas (transparency
through EffectComposer = black). Instead render **two scenes in ONE composer**:
```
const bloomPass = new UnrealBloomPass(...);            // keep the ref so the dive can ramp it
composer.addPass(new RenderPass(goldScene, goldCam));   // 1) gold backdrop (own STATIC cam), clears
const kdPass = new RenderPass(scene, camera);           // 2) KD hero on top
kdPass.clear = false; kdPass.clearDepth = true;         //    keep gold colour, clear depth → KD always in front
composer.addPass(kdPass);
composer.addPass(bloomPass);
```
- KD `scene.background = null` (so the gold shows through). `goldCam` is fixed at z=120 w/ gentle mouse parallax (does NOT orbit) → the gold looks right from any KD-camera angle.
- Backdrop = dispersed gold particle layers only (fine ~6500 / mid ~1400 / big-soft-bokeh ~280), **no ribbons**, pushed **far back (z≈-200)**, **dim** (opacity ~0.34/0.26/0.13, gentle sin-shimmer) so the brighter KD (opacity 0.95) clearly out-ranks it. Sizes scale up (~2.3/5.5/28) to stay visible at distance.
- Perf: 60fps desktop AND mobile verified (mobile counts ~0.6×, dpr cap 1.5).

## Why ribbons went to a FLAGSHIP, not the hero
Bright flowing gold **ribbons** in the hero's space = gold-on-gold that competes with the KD particles +
they smear under the orbiting camera. **Rule: never put a competing visual in the KD hero's space, showcase it as its OWN flagship instead.** → the ribbon scene became **AURA** (`kd-aura.vercel.app`),
a flagship card on the home grid + services, dived-into like AUREO/LUMO. The gold scene engine = the
`preview-golddrop` / `kd-aura` index.html (ribbons = dense tight-perp point-streaks clustered into a
central band + the 3 bokeh layers + bloom; faithful to `backdrop_gold.png`).

## 3D dive-into-flagship transition
On a `data-warp` click, instead of the flat 2D warp, fly the camera IN:
- State: `let diving3d=false, dive3dT0=0; const _diveTarget=new THREE.Vector3(0,0,12);`
- `warpTo()` sets `diving3d=true; dive3dT0=performance.now();` and navigates after **800ms**.
- In `frame()`, after the normal camera block: `if(diving3d){ const k=clamp((now-dive3dT0)/800,0,1), e=k*k*(3-2*k); camera.position.lerp(_diveTarget,e*0.92); camera.lookAt(0,0,-40); bloomPass.strength=0.32+e*1.9; renderer.toneMappingExposure=1.04+e*0.6; goldCam.position.z=lerp(120,6,e); }`
- `resetWarp()` (on `pageshow`) clears `diving3d`, restores `bloomPass.strength=0.32` + exposure=1.04 → no stuck state on Back.
- TODO (when the destination pages are designed): a matching "arrival" dive-out so home→page2 feels unbroken.

## QA loop (King wants this every "are we done")
- Programmatic (headed real-GPU Playwright, fresh load per width 1280/390/360): 0 console+page errors across the journey; 0 horizontal overflow; collect every `a[data-warp]` href + HTTP-check each resolves 200; loop reset (scroll to bottom → scrollY 0); dive fires + lands + Back resets.
- **fps must be measured FOCUSED**, a backgrounded MCP tab throttles rAF to ~1fps (false alarm). Use a dedicated headed page; the site = 60fps desktop + true-mobile.
- Mobile fit: measure `#b-work`.getBoundingClientRect, beat top must be ≥ nav height and bottom ≤ innerHeight (tall grids overflow a centered beat → collide with the nav). Fix by compacting cards on mobile (hide `.card .d`, shorter thumbs, tighter meta).

## ⚠️ Gold field must SPAN THE FRUSTUM at any aspect (the "one side black" bug)
- A **fixed-width** particle box (e.g. sx=380) is narrower than a wide desktop frustum → gold
  only fills the centre/one side, rest goes **black**. (Narrow phones hid it, the box was wider
  than the phone frustum.) King: "gold studio lights one side, other side black, should be all round."
- Fix = make the field width track the screen aspect, with constant density:
  `const _asp=innerWidth/innerHeight; const FW=Math.min(Math.max(2*(156*_asp+90),440),1600), FH=620;`
  then particle counts ∝ FW (e.g. `gLayer(Math.round(FW*14*dm), FW, FH, ...)`), `hx=FW/2` for drift wrap.
  (156 ≈ frustum half-height = tan(fov/2)*camDist for goldCam z=120, plane z≈-200.) → fills the whole
  frame, all around, at 1900-wide AND 390 mobile, 60fps. Keep parallax margin (+90) > parallax shift (mx*16).
- Computed once at init (no resize rebuild), fine for a single view.

## Other kd-site-v3 wins (2026-06-10)
- **Blurred env PNG → JPG**: `env_studio.png` 510KB → `env_studio.jpg` 42KB via `ffmpeg -i x.png -q:v 4 x.jpg`
  (visually identical because it's a blurred background/env map). Don't JPG images that need real alpha.
- **no-cache headers** so a stale HTML can't stick: `vercel.json` → `{"headers":[{"source":"/","headers":[{"key":"Cache-Control","value":"no-cache, must-revalidate"}]},{"source":"/(.*)\\.html",...}]}`.
- **og:/twitter share tags** on both pages (rich link previews for outreach), point og:image at a flagship thumb.
