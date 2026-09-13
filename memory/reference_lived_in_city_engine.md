---
name: reference-lived-in-city-engine
description: "The AUREO engine: a real-time low-poly Three.js NEON CITY you fly through on scroll, made photoreal + lived-in by stacking AI-image flat surfaces + recognisable low-poly movers + proper roadworks + venues + crowds. Proven on kd-aureo.vercel.app (King approved 2026-06-09). Reusable method + gotchas."
metadata:
  node_type: memory
  type: reference
  originSessionId: aureo-2026-06-09
  modified: 2026-09-12T14:28:41.930Z
---

**AUREO = King's finished city flagship.** File `C:\Users\Dell\OneDrive\Documents\Website Builder\replicas\aureo\index.html` (Three.js, **641 lines, 54.5 KB, dated 9 Jun 2026**, the day he approved it). LIVE **kd-aureo.vercel.app**, verified answering HTTP 200 on 12 Sep 2026.

**PATH CORRECTED 12 Sep 2026.** This line recorded `Documents\Website Builder\...` with no `OneDrive` in it, and nothing is at that path. Found only by searching the machine while opening Stage 7, which rests on reusing this file. The line count was also wrong, recorded as about 520 against a real 641. Verified genuine by its own markers from the recipe below: CatmullRom camera path, InstancedMesh movers, VENUES and CLEARINGS, UnrealBloom, Reflector, Lenis. Nine of his own `send_aureo_*.py` QA scripts sit beside it. Genre = SBS Town / open-sbs.brig.ht ([[reference-sbs-town-city-flythrough]]). Camera flies a CatmullRom path on TRUE scroll (Lenis); merged city = ~2 draw calls.

## The recipe that made it photoreal + alive (reuse this)
1. **Flat surfaces = AI images, not geometry.** Sky, listing photo, billboards are Gemini images (`tools\gemini_image.py`, model `gemini-3-pro-image`). Moving 3D objects (cars/boats/people) can NOT be images → use recognisable low-poly geometry instead. (This is the answer to "can a better Gemini image make them realistic?", no, geometry does.)
2. **Photoreal SKY transition (golden→dusk→night on scroll):** generate 3 EQUIRECTANGULAR sky-only HDRIs ("equirectangular 360 panorama, sky only, ... , 2:1"). A big `SphereGeometry` sky dome with a raw `ShaderMaterial` (BackSide, depthTest:false, renderOrder -1) samples all 3 by equirect UV (`u=atan(d.z,d.x)/2π+0.5; v=asin(d.y)/π+0.5`) and blends with two scroll mix uniforms `mGD=smooth(p/0.40)`, `mDN=smooth((p-0.42)/0.30)`. Dome `position.copy(camera.position)` each frame. Raw shader is NOT tone-mapped → shows the photo as captured. Hide 3D moon/aurora (photo carries them). Fog colour lerps the same 3 moods.
3. **Recognisable low-poly movers:** car = body box + cabin box (merged), `MeshStandard` + real car colours via `setColorAt`; boat = hull box + cabin box; person = legs cylinder + torso cylinder + head sphere (merged). All `InstancedMesh`, `frustumCulled=false`, matrices updated per frame. Per-instance SCALE (kids 0.6) via `m.makeRotationY(a); m.scale(sv.set(s,s,s)); m.setPosition(...)`.
4. **Proper ROADWORKS:** asphalt road decks (dark boxes) + pavements (lighter wider boxes) + glowing lane lines along the grid lines (multiples of 60). Car lanes already sit on those lines. River = a flattened canal LOWERED below the decks (`position.y=-1.0`) so the **opaque decks occlude it at crossings = bridges**; cars ride the decks (`y=0.2`), never the water. Keep generic buildings off road lines (they already skip `gx%4==0`).
5. **Lived-in VENUES + crowds:** an array `VENUES=[{t,x,z,c,k,w,h,d}]` (school/hospital/police/mall/bank/gym/bar/shops/stalls/cafe) placed in block gaps, added to `CLEARINGS` so generic buildings avoid them. Each = building + glowing roof band + accent ground pad + small camera-facing canvas-text SIGN that fades by distance; school gets a green pitch, hospital a white cross. People cluster `{x,z,r,rMin,kids}` AROUND every venue + districts, `rMin` keeps them in a ring on the pavement (never inside the building or the gold tower). Walkers wander between rMin..r (turn inward at outer edge, outward if they hit the building). **Orderly traffic:** each direction offsets to its own side (`z/x ± 2`) and faces its travel way (`ry` from `sp` sign) → no head-on overlap.

## Performance (hit 60fps on real phones)
- Merge everything possible; cap `dpr` (2 desktop / 1.4 mobile). Mobile (`matchMedia('(max-width:820px)')`) strips **UnrealBloom + Reflector** (uses a glossy plane) and uses fewer buildings/cars/people/stars.
- Reflector (wet streets) is the biggest desktop cost → 512² is plenty (1024² is wasteful).
- **NEVER read `el.offsetWidth` in the rAF loop** (layout thrash), cache label dims once.
- Optimize image payload: PNG→progressive JPG, resize (skies 1280w, billboards 720w) → AUREO went 4.4MB→346KB, load ~1.2s.
- **FPS is NOT measurable from the Playwright/headless browser** (it throttles rAF to ~2fps for ANY page, even blank), load/memory/layout/clipping ARE measurable; verify true 60fps on a real device.

## QA loop that catches overlaps (King's standard)
Screenshot every scroll stage (intro/wide/mid/dive/listing/finale) on **desktop + tablet 820 + iPhone 390**, READ each shot, hunt overlaps/clipping/floating/intersection, fix, redeploy, re-shoot, loop until ZERO. Real overlaps caught + fixed on AUREO: holo dome through cyan towers (ring the towers), people inside buildings (rMin ring), oversized venue signs (shrink), cars driving on the river (roadworks/bridges). Lenis hijacks scroll → use the force-hold trick to hold a scroll stage: `evaluate(()=>{const y=max*P;let n=0;const id=setInterval(()=>{scrollTo(0,y);if(++n>90)clearInterval(id)},35)})` then wait ~2s then screenshot.

## Deploy
`vercel deploy "<aureo dir>" --prod --yes` → take the `aureo-*-king-david-s-projects2.vercel.app` URL → `vercel alias set <that> kd-aureo.vercel.app`. New Vercel projects need ssoProtection disabled. Build originals, not clones ([[feedback-build-originals-not-clones]]).
