---
name: reference-ultimate-website-layered-method
description: "The 4-layer recipe for a top-tier immersive scroll site ('the ultimate website'): moving-bg Seedance video + many original images + real Three.js 3D + GSAP/Lenis long optimized scroll. Realism/immersion fixes for the rejected short cinematic templates."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c5d1dd4c-61db-477b-8314-0bd126c8ffbc
---

# The "ultimate website" · 4-layer immersive method

King's bar (from loving 8bit.ai / open-sbs city): a long, deep scroll where the **background is always moving**, the **story unfolds as you scroll**, there's **rich detail**, and it stays **buttery / no-lag even on mobile**. The earlier single-short-video cinematic templates (HALCYON, POMPOM) were REJECTED for being too short + not immersive + the AI image not realistic enough.

## The fix = stack 4 layers (don't rely on one short video)
- **A, living background:** a Seedance clip as a FIXED, continuously-moving backdrop behind everything.
- **B, story images:** MANY original Nano Banana images (8-12) that animate in as full-screen acts on scroll (parallax). More images = longer/deeper scroll.
- **C, 3D smart code:** a real Three.js object in the hero (glossy shapes, PBR + HDRI + soft shadows + subtle bloom) that reacts to mouse + scroll. NOT flat/gamey primitives.
- **D, glue:** GSAP ScrollTrigger + Lenis (smooth scroll-jack, kinetic per-word type, transitions). Target ~1000-1200vh, 8-12 acts.

## Hard requirements
- **Realism gate (for photoreal genres like a city):** generate a genuinely PHOTOREAL image first (push the prompt hard: "photorealistic drone photograph, real, no CGI/illustration look") and VERIFY it before use. Proven: the BoI Dublin aerial (`replicas\boi-city\assets\hero.png`) came out photoreal; the earlier stylized one did not.
- **Asset gate (King's rule):** generate images, show King, get his quality approval BEFORE building the site.
- **Optimization:** cap dpr (<=2, 1.5 mobile), dirty-check redraw, pause RAF when hidden, reduce/disable 3D on small screens, no heavy live blur over canvas. 60fps both widths.
- **Original, not a clone**, see [[feedback-build-originals-not-clones]].

## Tools / reuse
`tools\kie_generate.py` (Nano Banana image + Seedance video) · `/gsap` skill · Lenis+canvas+perf patterns in `replicas\halcyon\index.html` + [[reference-whole-page-cinematic-engine]] · Vercel deploy+alias. First live build of this method: the Claude-AI flagship (`replicas\claude-studio\`, plan `plans\cozy-chasing-quilt.md`).
