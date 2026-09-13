---
name: reference-immersive-morph-site-method
description: "The build method for the flagship immersive 3D morphing flythrough site (the /immersive-site skill). One particle cloud morphs through many worlds on scroll. Proof: Lumo = kd-claude-studio.vercel.app (King loved it 2026-06-09)."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 972bb7d5-c2f9-41f3-9f4b-37ce8c5e2ffd
---

The flagship web tier: an 8bit-genre, one-continuous-scroll, real-time 3D experience. Skill = [[immersive-site]]. Proof = **Lumo** (`Documents\Website Builder\replicas\claude-studio\index.html`, kd-claude-studio.vercel.app).

**The key idea (why it's both wow AND fast):** ONE `THREE.Points` cloud. Precompute a target position array per "world" (galaxy spiral, city towers, ocean wave-field, network nodes+links, core sphere). Each frame, **lerp every point between the current and next world's targets** based on scroll progress → the particles literally re-form from one world into the next (the morph), and it's one cheap system (great on mobile). Lerp colour per world too (galaxy orange, city blue, ocean teal, network violet, core orange).

**Gotchas / hard-won lessons (all from the Lumo session):**
- Progress MUST read `window.scrollY/(scrollHeight-innerHeight)` each frame (`readScroll()`), NOT Lenis's scroll event, the event under-reported and the journey lagged ~3x behind the scrollbar.
- Double-smoothing = lag: keep the extra `p += (rawP-p)*0.16` lerp snappy (~0.16), let Lenis do the smoothing.
- Loop must be SEAMLESS, not a rewind: at bottom, cover with a cream flash then INSTANT `scrollTo(0,{immediate:true})` (`doLoop()`), don't animate backwards.
- Background must move when IDLE (King flagged "bg isn't moving"): continuous shimmer/flow + slow camera drift, independent of scroll.
- Mobile perf is a HARD rule: dpr=1, ~3.2k points (9k desktop), NO bloom on mobile, `powerPreference:'high-performance'`, pause RAF when hidden.
- Bloom = EffectComposer + UnrealBloomPass (three@0.128 examples/js via CDN), desktop only, wrapped in try/catch so it never breaks the page. Bloom can blow out bright worlds (galaxy/core), tune strength/threshold to taste.
- Camera: orbit the cloud for worlds, fly-through for the tunnel, blend at the seam.
- Interactions: pointer parallax on the whole cloud (cheap, reads as "follows you"), drag→spin momentum on the core, tap→burst sprite pool, WebAudio drone+chime muted by default + toggle.
- Product feel = an HTML/CSS app-mockup overlay (crisp, zero asset cost), not a generated image.
- Stills (if needed) come from `tools\gemini_image.py` (Gemini = same model as KIE's "Nano Banana", cheaper/free-tier; KIE Seedance only when real VIDEO is truly needed). Build ORIGINALS, never clones.
