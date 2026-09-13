---
name: reference-immersive-chapters-engine
description: "The reusable engine + gotchas for King's kd-site-v3: studio-lights 3D bg, cinematic full-screen chapters with auto-scroll VIDEO previews, gold PARTICLE warp, deep-link fix, perf, demo-clip recording. Built 2026-06-09."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c90f00d8-8817-4f71-9a99-a3894ff35391
---

# Immersive Chapters Engine (kd-site-v3 method)

The pattern behind King's personal site + Services/Demos page. Files: `Documents\Website Builder\kd-site-v3\index.html` (home) + `services.html` (chapters). Three.js **r160 ESM**.

## Background · "black + gold + particles + STUDIO LIGHTS all over"
- King's locked look = **deep black with soft gold studio-light beams + gold bokeh, wrapping all around** (NOT a nebula, NOT blown out).
- Build: a Gemini equirect HDRI `assets/env_studio.png` (prompt = "equirectangular 360, black studio space, soft golden studio light beams + spotlights from many directions, gold bokeh particles all around, mostly black with glowing gold"). Use as `scene.background` + `scene.environment` (PMREM).
- **Params that look right (not blown out):** `backgroundBlurriness ≈ 0.46`, `backgroundIntensity ≈ 0.66`, **bloom strength ≈ 0.26, 0.32, threshold ≈ 0.9** (high threshold = only the brightest blooms), `toneMappingExposure ≈ 0.95`. Soften the grain-shader vignette to `mix(0.86,1.0,v)` so corners aren't black.
- **GOTCHA:** high intensity (>1.0) + low bloom threshold + ACESFilmic = a **blown-out yellow blob** where a bright spotlight faces the camera. Dim + raise threshold + blur to fix. (King flagged this; fixed by the params above.)
- Gold **dust point cloud** on top = the "particles" (additive, slow rotation, mouse parallax).

## Layout · cinematic full-screen CHAPTERS (the Services/Demos page)
- Each service = `<section class="chapter">` min-height 100svh: head (kicker/title/blurb) + **one featured demo** + a `.mrow` of smaller thumbnail demos. Scroll through like a journey. **No scroll-snap** (it felt janky, removed).
- **Featured preview = auto-scroll VIDEO** (`<video muted loop playsinline preload=none poster=thumb>`), played **only while in view** via IntersectionObserver (smooth + battery). Smaller demos = thumbnail `<a class="mcard">`.
- Data-driven: a `SECTIONS` array of `{id,k,t,p,feat,more,(aud),(cta)}` + a `D` demo map. Newsletter has no demo → a CTA.

## Demo-clip recording (the video previews)
- `tools\record_clips_2026-06-09.py`: Playwright `record_video_dir` → navigate each demo, smooth-scroll 0→bottom over ~7s → close (finalizes webm) → **ffmpeg** trims (`-ss 2.2 -t 6`), scales 720w, 24fps, no audio, crf 30, faststart → `assets/clips/<slug>.mp4` (20, 117KB).
- **GOTCHA: heavy WebGL sites record BLACK** (Playwright's video pipeline misses some WebGL). AUREO came out black → use its **still** instead (`NOVID = new Set(["aureo"])`, render `<img>` not `<video>`). Lighter WebGL (LUMINA) recorded fine. Always extract a check-frame with ffmpeg before trusting a clip.

## Cinematic PARTICLE warp (dive into a demo)
- `<canvas id="warp">`; on click of `a[data-warp]`: spawn ~170 gold particles streaking **out from the tap** + an expanding radial gold glow, draw on rAF for ~700ms, then `location.href=url` at ~660ms (**same window** = continuous journey). Add `body.diving` (zoom + brighten) for the dive.
- Mark links with `data-warp` (demos, flagships, pills, seelinks, back/brand). Book-a-call/email/mailto stay normal.

## CRITICAL FIXES (don't regress)
- **Back/forward glitch:** the page can restore from bfcache with `body.diving`/warp still on → looks stuck. Fix: `addEventListener('pageshow', resetWarp)` (clears diving + clears the canvas + `warping=false`).
- **Deep-link landing:** chapters are **built by JS**, so a `services.html#saas` jump fires before the section exists → lands at top. Fix: after `render()`, `if(location.hash){ setTimeout(()=>document.querySelector(location.hash)?.scrollIntoView(), 80); }`.
- **Scroll lag:** lighter 3D (fewer particles, dpr cap 1.2, 1.4, **half-res bloom**, **~30fps cap** on the ambient bg) + **pause `video.fv` during scroll**, resume the in-view one on scroll-idle (~170ms). Video-decode-during-scroll is the main lag.
- **Mobile tap targets:** tiny text links (seelink/back/brand) get an invisible `::after{position:absolute;inset:-14px}` to enlarge the touch area without changing the look.

## QA method (run every round)
- Headed/headless Playwright over a **local http server** (file:// blocks WebGL textures via CORS, always serve `python -m http.server`). Tools: `qa_interact`, `qa_buttons`, `qa_chapters`, `qa_final_3x`.
- Check: 0 console errors, no horizontal overflow (1280 + 390 + 360), every link href valid + HTTP<400, **every `#section` deep-link lands (top≈0)**, warp nav lands on the right URL (real `pg.click` / `pg.tap`, a **real gesture**; `location.href` via `evaluate` does NOT navigate in this harness), Book-a-call popup → cal.com, videos play in-view, ~60fps.
- **Home flagship cards are scroll-driven** (fixed beats) → Playwright coordinate-clicks are flaky (the card moves). Not a real bug; the same warp/nav works everywhere else + real taps.

## Delivery
- Deploy `cd kd-site-v3` → `vercel --prod --yes` (team king-david-s-projects2) → alias auto = kd-site-v3.vercel.app. **Never the domain until King says GO.**
- Always email (3 inboxes) + ntfy push **and** paste the link in chat. See [[feedback-always-send-gmail-and-link]].
