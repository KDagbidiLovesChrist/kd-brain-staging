---
name: reference-kd-launch-video
description: "How the KingDavid launch video is built in HyperFrames, the concrete method, the demo-capture pipeline, the 5-agent premium-upgrade pattern, and the hard-won render gotchas (esp. the immediateRender bug). Read before touching any HyperFrames video."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-launch-2026-06-07
---

# KD Launch Video · build method + gotchas (HyperFrames)

Project: `Documents\hyperframes-editor\video-projects\kd-launch\`. 9:16 (1080x1920), ~60s, black+gold cinematic.
Structure: `index.html` (master timeline: 7 scene divs + audio + nebula `#bgfx` + cinematic-grade overlays) loads
`compositions/s1-hook … s7-cta.html` (each a `<template id="X-template">` with a paused GSAP timeline registered to
`window.__timelines["X"]`). Recipe: Hook → Brand → Who → 8 Services (browser-window demos) → Proof → Goal → CTA(domain).

## Voiceover (George, ElevenLabs)
- `tools\regen_vo.py` POSTs the script to `/v1/text-to-speech/JBFqnCBsd6RMkjVDRZzb/with-timestamps` (voice=George),
  dynamic settings (stability 0.32, style 0.35, similarity 0.8, speaker_boost), model eleven_multilingual_v2.
- Decodes audio_base64 → `assets\george-vo.mp3`; converts char alignment → `assets\words.json` `[{w,s,e}]`.
- Pace lines with SSML `<break time="x.xs" />`. **GOTCHA:** the break tags come back in the alignment as fake "words"
  (`<break`, `time="3.0s"`, `/>`), filter those tokens out of words.json (regen_vo.py already does).
- Every scene's internal element timings + index.html scene `data-start`/`data-duration` + the `cuts[]` array are timed
  to the printed word timings. ElevenLabs key is TTS-scoped (401 on /v1/user is normal). Key in `.env.master`.

## Demo footage capture (the "footage is the hero" pipeline)
- `tools\capture_round2.py` (Playwright). Capture at **device_scale_factor=2** (retina sharp).
- **Normal DOM sites** (rivella, nexa, ascend, video-samples, lead-finder, relay): headless `full_page` → tall image →
  scroll via `translateY`.
- **WebGL flagships** (nova, kin = the `-animated` deploys nova-animated.vercel.app / kin-animated.vercel.app): render
  BLACK headless → must capture **HEADED** (headless=False). They're ~11000px scroll-scrub; grab a tall hero viewport
  (1280x1500) screenshot. Crop the bottom ~8% with ffmpeg to remove the "From EUR 4,000" pricing badge.
- In `s4-services.html` each demo is a browser-window card (gold bar + 3 dots + url pill); scroll demos use a
  `<img class="scrollimg" style="height:<h>px">` taller than the 612px body, animated `y: 0 → -travel` with ease "none"
  (LINEAR = smooth, the thing King insisted on). `travel` is capped per-demo so tall sites don't race. Single-screen
  apps (rivella chat, relay dashboard) use object-fit cover + a gentle scale zoom instead.

## ⚠️ THE immediateRender BUG (the "thick gold circle" · took ~6 render cycles to find)
GSAP `fromTo` defaults to `immediateRender:true` → it applies the **'from' values at build time**, so any OVERLAY
(flash / whip / burst / light-sweep) whose 'from' opacity is VISIBLE (e.g. 0.44) shows from frame ONE and only clears
after its own tween first runs. Symptom: a gold radial glow over ONLY the FIRST demo (it cleared after the first cut).
We chased the nebula orb for ages (z-index covers, source-fade), none worked because it wasn't the orb.
**FIX: add `immediateRender:false` to every overlay `fromTo` that has a visible from-state.** Applies to s2/s3/s4/s5
flashes + the s4 whip. This is now a hard rule in every agent brief.

## Cinematic grade (index.html, atmosphere only)
A colorist agent added: richer warm `.sky`/`.neb`/`.orb`, anamorphic two-layer `.vignette`, refined overlay-blend
`.grain`, and new decorative layers `.lens-bloom` / `.light-leak` / `.ana-streak` (slow CSS @keyframes, no JS) +
a top `.cgrade-wash` (z-31, soft-light, ~0.1) and `.ana-bars` letterbox. Grade applies to the WHOLE film once
`#scene-4` z-index is dropped to 14 (normal order), it was 35 (an earlier failed orb-glow fix; no longer needed since
`#bgfx` is faded to 0 during services + scene-4 has its own opaque bg). Keep grade subtle so demos stay legible.

## The 5-agent premium-upgrade pattern (King asked: "5 agents make it much better")
- Launch 5 Sonnet sub-agents IN PARALLEL, each owning ONE distinct file (no collision): Hook(s1) / Services(s4) /
  Early-text(s2+s3) / Closing-text(s5+s6+s7) / Art-director(index.html grade).
- Each agent gets: exact VO beat timings, current file, the HyperFrames hard rules (template wrapper, register timeline,
  only animate transform/opacity/filter/clipPath, immediateRender:false on overlays, no Math.random/repeat:-1, embedded
  fonts), brand palette, and a premium brief. Agents edit BLIND (no render).
- LEAD (me) then: lint → integrate → draft render → frame-QA EVERY beat → fix → high render → deliver. Worked cleanly
  (0 lint errors, no broken scenes). This is a reusable money-asset upgrade method.

## Render + delivery
- `npx hyperframes lint` then `npx hyperframes render --quality draft|high --output renders/<name>.mp4` (FOREGROUND only;
  ~3min draft / ~7min high for 60s). Frame-QA via ffmpeg `-ss <t> -frames:v 1` then Read the jpg.
- Deliver: compress with ffmpeg (crf ~25-26, faststart) to <24MB for Gmail; `tools\send_launch_video.py` (Gmail API,
  token at `.claude\token.json`, sends to King's 3 inboxes). Host on **kd-review.vercel.app** (`Documents\Website
  Builder\kd-review\`, edit index.html top card + copy mp4 in + `vercel --prod`). Open locally with Start-Process.
- Gemini can WATCH a render for a second opinion: `tools\gemini_watch_local.py --file <mp4>`.

## v3 upgrade (2026-06-07) · the 15-voice consensus rebuild + sound design + brightness
- **15-agent consensus-review pattern (King asked for it):** extract a labelled frame-strip (ffmpeg `fps=1/2,scale` →
  `tile=5x2` contact sheets + a few full-res key frames) from the ACTUAL render so critics judge output not code → launch N
  read-only critic sub-agents (Sonnet), each owning ONE criterion (hook / cut rhythm / time-to-value / brightness /
  hero-framing / captions / grade / motion-gfx / transitions / sound / brand / script / energy / demo-order / CTA) → each
  returns SCORE + PREDICTION + timecoded FIXES + SEVERITY → lead synthesizes the consensus → implements. Reviewers DON'T
  collide (read-only) so the count can be high (15); builders must be per-file. v2 scored 5.4/10: slow start, work too
  small + too dark, no sound design, quiet ending.
- **Sound design = the single biggest "now it feels edited" win.** Build ONE pre-mixed SFX track `assets/sfx.wav` with
  `tools/build_sfx.py`: generate base clips (whoosh = pink-noise burst w/ envelope; chime = two-tone sine w/ decay; riser =
  rising noise swell), then place copies at exact timestamps via ffmpeg `adelay=ms|ms,volume=g` + `amix=inputs=N:normalize=0`
  anchored by an `anullsrc` base of full length. Add as ONE extra `<audio data-track-index="9">` (don't use many tags). Cues:
  whoosh on every scene+demo cut, chime on every demo label, riser into the CTA, impact on "Free.". Duck music 0.16→0.10.
- **Brightness:** per-demo inline `filter:brightness(...)` on the demo `<img>` (overrides the global `.body img`), dark
  sites ~1.4, bright (relay/ascend) ~1.0-1.1; AND GSAP-tween the master `.vignette` + `.cgrade-wash` opacity DOWN during the
  services window (e.g. 13.7→39.0) so the grade lifts off the work then returns for the text scenes.
- **Footage as hero:** move the browser card up + grow `.body` height (612→700), recompute scroll `travel = ~h-bodyH`
  (capped per-demo so tall sites don't race), bump caption font (39→46, weight 600). Kill the dead black band.
- **Faster start:** rewrite the intro shorter (cut the "A trade / A shop / A startup" list → one line), regen VO, retime,   first demo lands ~14s of audio (was 17.4). Keep service order/wording stable so mostly the intro shifts (lower risk).
- v3 timeline: s1 0-5.3 / s2 5.3-10.9 / s3(who="Every business. One advantage.") 10.9-14.0 / s4 14.0-39.3 / s5 39.3-43.6 /
  s6 43.6-47.1 / s7 47.1-54.5. Total 54.5s. Backups: `george-vo-v2.mp3`, `words-v2.json`, `index-v2.bak`, `s4-services-v2.bak`.
- Known soft spot: the CONTENT (video-samples / yourbrand.media) demo is an all-dark video-showcase page, no capture is
  bright; brightness lift helps but it stays the weakest demo. Swap for a brighter content proof if perfection needed.

## v3.1 (2026-06-07) · live 3D-scroll demo, active AI chat, content grid, 4K
- **Embedding a moving site demo (e.g. a WebGL/3D scroll-scrub) inside a browser-card: use a TOP-LEVEL `<video>`, NOT an
  in-card one.** A `<video data-start="X">` placed INSIDE a sub-composition template renders BLACK, HyperFrames treats the
  element's `data-start` as ABSOLUTE master time, so a sub-comp-relative value (0.14) gates the clip to ~0-4s and hides it
  during the demo. FIX: put the `<video class=... data-start="<master time>" data-duration data-track-index muted playsinline
  src=...>` at the TOP LEVEL of index.html, absolutely positioned over the card body (match card body: left 66 top 340 w948
  h696, z-index 20 = above scene-4 z14, below grade overlays z28), `object-fit:cover`, border-radius bottom. Keep the static
  screenshot in the card as a fallback underlay. This is how the WEBSITES (nova) demo shows real 3D scrolling.
- **nova 3D scroll capture** (`tools/capture_final.py`): headed Playwright (WebGL=black headless), viewport ~1280x940 dsf2,
  scroll 0→scrollHeight in ~96 steps, screenshot each → `ffmpeg -framerate 24 -i f_%03d.jpg` → mp4. **CROP the bottom ~200px**
  (`crop=2560:1680:0:0`) to remove the fixed "From EUR 4,000 · Book a call" pricing badge (bottom-left), no pricing rule.
- **Active AI-assistant capture:** headed Playwright on the demo URL (ai-assistant-demo-blond.vercel.app), `get_by_text("Do
  you fix boilers?").click()`, wait ~7s for the real AI reply, screenshot → shows a live conversation (far clearer than the
  sparse greeting). Display zoom-cover.
- **Weak "CONTENT" demo fix:** the video-samples page is all-dark video players; the dark hero looked like a failed capture.
  Crop the page to the "One ad per service, eight ways I make it move" GRID section (`crop=2530:5400:0:4200` of the tall
  capture) → gold-bordered labelled tiles = reads as a real video portfolio. Scroll through it. brightness ~1.45.
- **One-more consensus = a focused 6-critic panel** (animation polish) on the new draft; honour King's "keep the breathing
  pauses/silences" (do NOT hard-cut the brand/proof dissolves, he says the silences make it sound articulate). Applied:
  content-grid swap, a wider gold corona on the "Free." slam (the peak frame), a gentle pill breathe. Skipped: per-number
  motion-graphics (fiddly to align over scrolling baked screenshots), cursor-click gimmick.
- **4K render:** `npx hyperframes render --quality high --resolution portrait-4k` (2160x3840; renders at 2x DPR, composition
  unchanged; aspect must match + be an integer multiple). Heavy (~3-4x the 1080 time) → run in BACKGROUND to avoid the 10-min
  Bash timeout. Then downscale to 1080 (crf 26) for Gmail/kd-review; 4K is the master.

## v3.6 (2026-06-07) · full-width demos, badge removal, true-30fps, VO artifact silencing
- **THE "left-crop" cause + clean fix (reusable).** A demo "cut off on the left" was NOT a scale bug, a ~12%
  centre-crop had been added in assembly to hide a FIXED bottom-left credit/price badge ("Flagship build by
  Kingdavid Agbidi · From EUR 4,000 · Book a call"). The crop ate the left edge ("OVA"/"IN"). **Don't crop to
  hide a fixed overlay, HIDE IT IN THE DOM and re-capture full-width.** `tools/cap_nova_kin_v36.py`: before
  scrolling, `page.evaluate` JS that finds any small (`textContent.length<140`) element matching
  `/Flagship build|Book a call|From\s*EUR|From\s*€/i`, climbs to its nearest fixed/absolute/sticky ancestor, and
  sets `display:none!important`. Then capture 2560×1880 frames and assemble `scale=1424:1044` with **NO crop**
  (capture ratio 1.362 already ≈ card 948×696). Result: full site + no pricing, no left-crop.
- **delogo is the WRONG tool for a fixed overlay over moving content**, it interpolates per-frame from
  surrounding pixels, so over a scrolling/bright area it SMEARS into a shifting blob (clean only on flat near-black).
  Verified by extracting a delogo'd frame and reading it. Use the DOM-hide re-capture instead.
- **Judder = frame duplication.** A clip assembled `-framerate 17 -r 30` duplicates frames to reach 30fps = visible
  judder. Fix: capture ENOUGH unique frames (≥ clip_seconds×30) and assemble `-framerate 30` (each output frame a
  distinct capture). nova 150 / KIN 120 unique frames → buttery. `ffprobe nb_frames` ≈ seconds×30 confirms.
- **Silencing a VO artifact surgically (can't listen → use waveform + silencedetect).** Find the word's end in
  `words.json`; run `ffmpeg -ss A -to B -i vo.mp3 -af silencedetect=noise=-38dB:d=0.07 -f null -` (NB: reported
  times are RELATIVE to the `-ss` trim, add A back). Non-silent spans inside the post-word gap = the artifact.
  Silence ONLY it: `-af "volume=enable='between(t,start,end)':volume=0"` with edges landing inside existing
  silence (no click). Confirm with `showwavespic` before/after and that `format=duration` is unchanged (keeps
  every word timing valid). v3.6: blips at 46.9-47.35s after "company." → muted [46.86,47.55].
- **Posters that match the clip (glitch fix preserved):** re-extract `ffmpeg -i clip.mp4 -frames:v 1 -q:v 2
  poster.jpeg`, MUST be `.jpeg` (the in-card `<img>` code appends `.jpeg`; a `.jpg` 404s → broken-image).
- Delivery unchanged: web copy `-crf 30` (got 6.7MB), `send_launch_video.py` (3 inboxes), kd-review (`?v=` bump +
  `vercel --prod --yes`, verify 200), Desktop 1080 + 4K (`scale=2160:3840:flags=lanczos -crf 20`).

Related: [[reference-hyperframes-video-method]] · [[feedback-video-quality-bar]] · [[feedback-edited-not-scroll]] · [[project-upcoming-tasks]]
