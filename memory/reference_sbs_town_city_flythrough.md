---
name: reference-sbs-town-city-flythrough
description: "King's long-lost 'bank/city' reference is SBS Town (open-sbs.brig.ht, by Studio Mirage), a real low-poly 3D neon city you fly through on scroll. His AUREO city flagship is built to MATCH this with real 3D geometry, NOT the Lumo particle engine."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c2025939-d9b7-4e21-8135-11716865b16b
---

**The reference King kept losing = SBS Town.**
- Live: **https://open-sbs.brig.ht/** (title "SBS Town"). Built by **Studio Mirage** (`studiomirage.io/works/sopra-banking`) + Bright, for Sopra Banking Software ("SBS" = his "open-sbs" clue).
- What it is: a **stylized low-poly 3D town**, real little buildings, roads, water around an island, glowing cyan coastline, mountains on the horizon, neon glow (purple/blue/pink/cyan). It opens **blurred (focus-pull/DOF)** with the logo + "scroll to continue"; as you scroll the **camera flies DOWN into the city** and you visit **labelled district buildings** (Regulatory, Financing, Innovation, Risks). Real 3D geometry you move through + clickable landmarks.

**THE LESSON (I missed twice before getting this right, 2026-06-09):**
- This genre is **real 3D city geometry**, NOT abstract particles. I first reused the **Lumo particle engine** for AUREO → King: "looks exactly like lumo… nothing like what I wanted." The Lumo morphing-particle engine is for ABSTRACT sites only; a city/bank flythrough needs actual modelled buildings.
- **Always find + actually SEE the reference before building** ([[feedback-discovery-intake-before-building]]). When a link is "lost," dig it out (Gmail self-emails, the building agency's portfolio, Bing, web.archive.org is blocked from WebFetch/WebSearch but the **Playwright MCP browser can load pages those can't**).

**AUREO build (the original, NOT a clone, [[feedback-build-originals-not-clones]]):** `Documents\Website Builder\replicas\aureo\index.html`, live **kd-aureo.vercel.app**. Procedural low-poly Three.js city: ~140 neon buildings (Box + EdgesGeometry, emissive) on a CircleGeometry island, glowing cyan coastline torus + road grid, distant cone mountains, **a gold landmark "AUREO Tower" at centre** (King chose "neon + gold blend"). Camera flies in via a `CatmullRomCurve3` position+look path driven by true scroll (`readScroll` reads window.scrollY, like Lumo). HTML district-label pills projected to screen each frame; focus-pull = a CSS `backdrop-filter:blur` overlay that clears by p≈0.06; UnrealBloom desktop-only; property listing card + outro + seamless loop. KIE was topped up 2026-06-09 (Seedance available again) but this build needs no credits.

**✅ COMPLETE + King-approved 2026-06-09 ("ok im happy").** AUREO grew into a full **lived-in, photoreal city**, photoreal golden→dusk→night sky, filled districts, venues (shops/school/hospital/police/mall/bank/gym/bar/stalls), crowds + kids, orderly traffic, proper roads+pavements+canal bridges, real apartment photo, LED art billboards. Perf-optimized (~1.2s load, 60fps on King's phone) + passed a strict multi-angle/multi-device clipping QA (zero issues). **Full reusable engine + method + gotchas: [[reference-lived-in-city-engine]].**
