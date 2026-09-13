---
name: skill-seedance-animated-websites
description: "The Nate Herk (AIS) method for premium 'animated 3D-style' websites that look $10-15k. AI cinematic video scrubbed frame-by-frame on scroll (NOT real-time WebGL). Pipeline + tools BUILT + PROVEN 2026-06-03. This is King's new flagship/highest-price web tier."
metadata: 
  node_type: memory
  type: project
  originSessionId: 47a394ac-c680-49cb-b8b8-a5eaab1d3948
---

# Seedance Animated Websites · the Nate Herk method (BUILT + PROVEN 2026-06-03)

After the hand-coded real-time WebGL 3D direction kept lagging + feeling like "AI slop" (King's words), we PIVOTED to **Nate Herk's AIS workflow** for premium "3D-style" websites. King: "this is how I want my 3D websites to be like." First site approved ("looks good").

## THE METHOD (why it's smooth + premium)
A cinematic AI **video** is **scrubbed frame-by-frame as you scroll** (the Apple-product-page technique). It LOOKS like 3D but is just images flipping → buttery smooth, NO real-time WebGL, NO lag, even on a phone. This is the key lesson: **don't make the whole page a live 3D world (laggy), use one contained cinematic clip scrubbed on scroll.**

## THE PIPELINE (per site, ~$1.33 in KIE credits)
1. **Nano Banana (image)** designs the hero still. KIE model `google/nano-banana` (NOTE: `google/nano-banana-2` is NOT on KIE → 422; v1 works great). ~$0.08.
2. **Seedance 2.0 (video)** animates that still into a cinematic clip. KIE model `bytedance/seedance-2` (also `bytedance/seedance-2-fast` = cheaper). Pass the still as `first_frame_url`. ~6s, 720p, `generate_audio:false`. ~$1.25.
3. **ffmpeg** extracts frames: `ffmpeg -i hero.mp4 -vf "fps=30,scale=1280:-1" -q:v 3 frames/f_%03d.jpg` (~180 frames).
4. **Build the site** with the **`frontend-design` skill** (see below): sticky `<canvas>` over a tall spacer (~500vh), preload frames, map scroll→frame index, `drawImage` cover. GSAP ScrollTrigger `scrub:1.0` OR lerp the frame index for buttery motion. Premium sections around it.
5. **Deploy** Vercel.

## TOOLS BUILT (all in `tools\`)
- `kie_generate.py`, `image "<prompt>" out.png [aspect]` / `video "<prompt>" out.mp4 [first_frame_url] [dur] [res] [aspect]`. Reads `KIE_AI_API_KEY` from `.env.master`. KIE API: POST `api.kie.ai/api/v1/jobs/createTask` {model,input}; poll GET `recordInfo?taskId=` → `data.state=='success'` → `JSON.parse(resultJson).resultUrls[0]`.
- `batch_seedance.py`, batch image+video for a list of concepts, 3 concurrent, logs to `seedance\batch_log.json`.
- `gemini_watch_workflow.py` / `gemini_watch_website.py` / `gemini_watch_motion.py`, Gemini 2.5-flash watches a YouTube URL or local mp4 and extracts workflow / website-recreate-spec / motion spec. Studies in `knowledge\video_studies\`.

## THE ARSENAL · `frontend-design` skill (King's AIS community arsenal)
Installed at `C:\Users\Dell\.claude\plugins\marketplaces\claude-plugins-official\plugins\frontend-design\skills\frontend-design\SKILL.md`. It is the premium-design RULEBOOK Nate uses: distinctive characterful typography (NO Inter/Arial/Space Grotesk), one bold cohesive aesthetic, atmosphere/depth, high-impact motion, literally "avoid generic AI slop." Each build agent is told to READ + FOLLOW it.

## STATUS (2026-06-03 night)
- **10 cinematic hero videos generated** in `Documents\Website Builder\seedance\<slug>\hero.mp4`: veyra, flux, nova, meridian, veloce, kin, lume, roast, atlas, orbit. (Creative/costly part DONE.)
- **VEYRA template proven** = `veyra-web-eight.vercel.app`.
- **3 VEYRA design directions live for King to pick:** A `veyra-a.vercel.app` (editorial maison), B `veyra-b.vercel.app` (dark cinematic), C `veyra-c.vercel.app/?v=2` (modern luxe). **Awaiting King's pick.**

## HARD-WON LESSONS
- **Mobile loader MUST reveal early + have a timeout**, waiting for ALL frames with no fallback HANGS on mobile (King hit "stuck at 000/145"). Fix: reveal on first frame (draw frame 0) + a 3.5s hard `setTimeout` fallback; keep loading the rest in background. Bake this into the template.
- **Tool-augmentation** (King's directive): pay for / connect APIs + MCPs instead of hand-coding hard things. KIE (Seedance/Nano Banana) = the video/image engine. [[feedback-tool-augmentation]]
- **Higgsfield** = best-in-class cinematic camera presets BUT separate platform, API is enterprise-gated, not on KIE → use selectively + manually (their web app) for a specific hero only; don't depend on it.
- **21st.dev (+ its "Magic" MCP)** = the premium component library Nate uses; worth connecting to level up the page sections (free tier + cheap paid). King open to it.
- **Vercel:** brand `<name>.vercel.app` aliases serve public; brand-new aliases can hit SSO-401; re-alias to a known-public name. Use `?v=N` to cache-bust for the user's phone.
- Each brand still gets its OWN look (don't reskin one template blindly) [[feedback-each-3d-world-truly-unique]], but the scroll-scrub ENGINE is reusable across the 10.

## NEXT
King picks A/B/C → lock as master template → roll across all 10 (videos ready) → 10 premium animated sites = the flagship €4k+ tier portfolio. Optionally regen the diamond at 1080p for max sharpness; optionally wire 21st.dev MCP. €0 earned; ~$13 KIE spent on the 10 videos.

## 2026-06-08 · RECONFIRMED as THE method (after a long 3D detour) + Elypt refs decoded
King sent 4 YouTube tutorials (mhIAd5lVMag, ZfYvv-0l9NA, q0TgUtj6vIs, TcFeSjwTo7g) + 4 screen-recordings of **Elypt-style** sites. All confirm: **this scroll-scrub method IS what the TikTok/YouTube "3D website" creators use** (Claude Code + Nano Banana + Seedance/Kling). **Hard rule from King: STOP hand-coding real-time 3D (Three.js/Spline), the quality came out bad. Use Nano Banana (images) + Seedance/Kling (cinematic video) scrubbed on scroll. Always.** (This session I wasted a long detour on Three.js igloo + Spline before landing back here, don't repeat it.)
- **Elypt's exact style** (Gemini studies in `knowledge\video_studies\2026-06-08_18-07-15...` (real-estate "VELLORA" journey) + `...18-09-26...` (interior "Spaces that breathe" furnishing room)): AI cinematic clip → ALL frames extracted → **sticky/pinned hero canvas, scrubbed on scroll**, with **elegant serif headline + "chapter" text overlays fading in at scroll %**, warm-neutral palette, Lenis smooth scroll. Longer clip = more frames = longer cinematic journey (interior→exterior, or empty→furnished).
- **NEW proof: SONA** = `kd-sona.vercel.app` (`Documents\Website Builder\replicas\sona\`), premium headphones that ROTATE as you scroll. Nano Banana still → Seedance rotation → 113 frames → canvas scroll-scrub + Lenis + serif headline + spec sections. Verified 200, 0 errors, renders headless. Built in minutes. This is the clean reusable template.
- Refs downloadable: King set the 4 Drive MP4s to "anyone with link"; pull via `curl -sL "https://drive.usercontent.google.com/download?id=<ID>&export=download&confirm=t"`. Files in `Documents\Website Builder\replicas\_refs\`.
- Skill to run it all = `/seedance-site`. King wants this as the reusable engine to build ANY site. Refinement to bake into the template: longer JOURNEY clips + timed serif chapter overlays (the Elypt signature), warm-neutral default, sticky-hero + tall spacer.
- Headless QA works for scroll-scrub (canvas+jpg), UNLIKE real-time WebGL (swiftshader mangles it), so I CAN self-verify these. Related: [[reference-photoreal-flagship-method]] (the photoreal-render-not-primitives lesson) · [[feedback-tool-augmentation]].
