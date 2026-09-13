---
name: feedback-no-handcoded-3d-cinematic-method
description: "HARD RULE (King, 2026-06-08): never hand-code real-time 3D for him (Three.js/Spline), quality comes out bad. ALWAYS use the AI-tool cinematic method: Nano Banana image + Seedance/Kling video scrubbed on scroll (= /seedance-site). Build any 'dramatic/3D/cinematic website' this way."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 24550801-85f6-4431-b91a-adc369bc8d43
---

# Don't hand-code 3D. Use the AI cinematic method. (King, hard rule 2026-06-08)

King, verbatim: *"I don't want you to try code it anymore. But when you code it, the quality comes out so bad. I rather you use tools like banana [Nano Banana], kling, seedance... for the best quality realistic and cinematic. Don't code it anymore."*

**The rule:** For ANY "3D / cinematic / dramatic / interactive" website request, do NOT hand-code real-time 3D (Three.js, hand-built WebGL, Spline scenes I can't author). Use the AI-tool pipeline instead:

1. **Claude** writes the brand, copy, and the image + video prompts.
2. **Nano Banana** (KIE `google/nano-banana`, 16:9, hi-res) → the realistic hero image. (NOTE: `google/nano-banana-2` 422s on KIE, use `google/nano-banana` directly so there's no error noise.)
3. **Seedance 2.0** (KIE `bytedance/seedance-2`, first_frame_url=image) or **Kling** → a cinematic clip. For drama = a real JOURNEY (e.g. interior→pool→villa reveal); stitch 2 clips with an ffmpeg `xfade` for a longer move.
4. **ffmpeg** extracts all frames.
5. **Build the site** (HTML/CSS/JS web layout is fine, that's not the "coding" he means): sticky hero `<canvas>` over a tall `heroWrap` (~460, 640vh), frames **scrubbed on scroll**, serif "chapter" text fading in at scroll %, Lenis smooth scroll, custom cursor.
6. **Deploy** Vercel (`--scope king-david-s-projects2`, PATCH `ssoProtection:null`, alias `kd-*`).

**Why:** this session burned a long detour hand-coding a Three.js igloo (kd-niva-3d) and a Spline attempt (kd-spline-test) and a procedural crystal (kd-prisma-3d), all rejected as low quality / "nothing like" the reference. The scroll-scrub AI method (kd-sona, kd-marea, kd-aether, kd-ascent) is what looks premium AND I can self-verify it (canvas+jpg renders correctly headless; real-time WebGL does not).

**How to apply:** the reusable skill is **`/seedance-site`**. Treat it as the one engine for "build any cinematic site we want." Don't copy a reference site's brand/assets, recreate the *method/drama* as King's own. Match the DRAMA of his Elypt refs (full journeys + chaptered serif text). Full method + proofs: [[skill-seedance-animated-websites]]. Boundary lesson: [[reference-photoreal-flagship-method]].
