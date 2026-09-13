---
name: feedback-hero-likeness-and-perf
description: "Three locked lessons from the 2026-06-04 hub session: (1) AI redraw alters King's face, for 'exactly him' use his real footage matted, but he ultimately preferred the original render; confirm before re-touching the hero. (2) CSS masks on scaled elements lag laptop GPUs, use border-radius + cull offscreen. (3) Every interactive element on his sites should have the Nate-style cursor 3D tilt + follow-glow."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: bc30d689-9b4e-4d56-a5d9-c9797ba65071
---

# Hero likeness + performance + interactive feel (2026-06-04)

## 1. His face: AI redraw ALTERS it
Running King's photo/frame through Nano Banana edit or Seedance **redraws the image → changes his face** ("why did my face change"). The only way to keep his EXACT face is to NOT run it through generative AI, **matte his real footage** (`best.mov`) with **rembg** (`u2net_human_seg`, segmentation keeps real pixels) and composite over a new background.
**Why:** generative models re-synthesize pixels; matting only masks them.
**How to apply:** for "make it exactly me," use the real-footage + matte pipeline (`tools\build_real_hero.py`), NOT AI re-render. BUT note: King saw the faithful matte version and still **preferred the original golden-cosmos `cosmic_right` render** (the cutout look + mirror + boomerang-reverse bothered him). **Don't change the hero again without asking**, he was frustrated by the back-and-forth. [[project-galaxy-hub]]

## 2. CSS masks on scaled elements lag laptops
`mask-image` (radial feather) on the planets, scaled every scroll frame, was smooth on his PHONE but **laggy on his LAPTOP** (weaker GPU, mask = extra render pass).
**Fix that worked:** `border-radius` circle-clip on **pre-cropped** images (no mask) + **cull offscreen elements** (`visibility:hidden` + `willChange:auto` when beyond the active window, only ~1-2 render) + drop continuous animations + cap video `playbackRate`.
**How to apply:** avoid `mask-image`/big blurred box-shadows on many scaled/animated layers; cull what's offscreen; transforms+opacity only.

## 3. Interactive "Nate Herk" feel = standard on ALL his sites
King wants every interactive element (cards, buttons) to have a **dynamic, professional, parallax feel on hover** like nateherk.com, a **cursor-following 3D tilt + a glow that follows the mouse**. Implemented on the hub as `.kd-glow` + a desktop mousemove tilt module in `app.js`.
**How to apply:** bake this cursor-tilt+glow into the galaxy template when rolling it to his other 3D sites. Desktop/hover only (guarded by `hover:hover`); off on touch.
