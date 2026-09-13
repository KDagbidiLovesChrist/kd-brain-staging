# /immersive-site · Build an 8bit-genre immersive 3D morphing flythrough website

**Trigger:** `/immersive-site`, or "build an immersive site / a flythrough site / an 8bit-style site / a morphing 3D scroll site / a site like Lumo".
**What it is:** the FLAGSHIP web tier, one continuous, scroll-driven, real-time 3D experience where a single particle cloud MORPHS through several "worlds" as you scroll, with cinematic glow, interactions and a believable product story. Proven build: **Lumo** (kd-claude-studio.vercel.app), loved by King 2026-06-09. €3k, 5k+ tier.

> **READ FIRST:** `C:\Users\Dell\.claude\CLAUDE.md` (esp. Rule #13 discovery-first + WAT) and the method memory `memory\reference_immersive_morph_site_method.md`.

---

## WAT chain
- **W (Workflow):** this file + the discovery interview below.
- **A (Agent):** Claude, in the role of a senior creative web/3D director, interviews King, designs, builds.
- **T (Tool):** Three.js r128 + EffectComposer/UnrealBloomPass + Lenis (all CDN) · Vercel deploy · Gemini image gen (`tools\gemini_image.py`, cheaper than KIE) only if stills are needed · `tools\push_kd.py` + `replicas\claude-studio\send_site_to_phone.py` for delivery.
- **S (Skill):** this `/immersive-site` command.
- **Money:** flagship proof piece → wins web/SaaS/creative clients; sellable at the top tier.

## STEP 1 · Discovery FIRST (never skip · Rule #13)
Take the expert role and interview King ONE topic at a time, explaining each in plain English and showing a PREVIEW (AskUserQuestion `preview` field with ASCII/visual mock, or a free live build) before locking. Ask about:
1. **Goal / what it sells** (portfolio piece? product launch? both?).
2. **Reference**, get the ACTUAL site/video and study it (watch video with `tools\gemini_watch_local.py`; live sites via Playwright; note WebGL sites screenshot black, so use the video). Don't guess.
3. **Worlds**, which scenes to morph through, and the order.
4. **Colours**, one palette vs per-world colour.
5. **Transitions**, seamless blend / warp-flash / morph / portal.
6. **Interactions**, drag objects, pointer-attract, tap-burst, sound.
7. **Product/story**, is there a fake app UI mockup + narrative?
8. **Constraints**, mobile perf (HARD: no lag), budget/credits, originality (build ORIGINALS, never clone, [[feedback-build-originals-not-clones]]).
Restate the brief, get the yes, build ONCE.

## STEP 2 · Build (copy + adapt `replicas\claude-studio\index.html`)
The engine pattern (see method memory for the full detail):
- **ONE `THREE.Points` cloud** (N≈9k desktop / ~3.2k mobile). Precompute a target Float32Array per world (galaxy spiral, city towers, ocean wave-field, network nodes+links, core fibonacci-sphere, etc.).
- **Morph = lerp** every point between the current and next world's targets, driven by true scroll progress (`readScroll()` reads `window.scrollY`, NOT the Lenis event, that lagged). Lerp colour per world too. Use a `STOPS` table mapping `p`→world.
- **Camera:** orbit the cloud for the worlds (radius shrinks toward the core), then switch to fly-through for the tunnel; blend at the seam.
- **Cinematic:** EffectComposer + UnrealBloomPass on **desktop only** (wrap in try/catch so failure never breaks the page); mobile uses raw additive-glow for speed.
- **Interactions:** pointer parallax on the cloud, drag→spin momentum on the core, tap→burst sprite pool, WebAudio drone+chime (muted by default + toggle button).
- **Product:** chat/UI mockup as an HTML/CSS overlay (crisp, zero asset cost) fading in on its beat.
- **Keep:** warp-in cream flash, ripple/core-burst + mark reveal, textured tunnel cylinder, cream outro with the **"Designed & built by Kingdavid Agbidi" + hire-me CTA**, and the **seamless loop** (`doLoop()` = flash-covered instant jump to top, NO rewind).
- **Perf (hard rule):** dpr 1 mobile / 2 desktop, fewer points + no bloom on mobile, `powerPreference:'high-performance'`, pause RAF when tab hidden, continuous flow/shimmer so the bg is alive when idle.

## STEP 3 · Deploy + QA
`vercel deploy --prod --yes` → `vercel alias set <prod> <slug>.vercel.app`; disable `ssoProtection` via the Vercel API if it 401s (PATCH `/v9/projects/<name>` `{"ssoProtection":null}` with `VERCEL_TOKEN`). QA with Playwright at 1440 + 390: every world paints + morphs (sample beat opacities via DOM), 0 console errors, no horizontal overflow, idle frames differ (bg moving), outro+CTA + loop work.

## STEP 4 · Deliver (Rule: always Gmail + link)
Email the live link + 2, 3 screenshots to King's Gmail (+iCloud/Yahoo) via the send-script pattern, ntfy push, AND paste the link in chat. Then iterate on his real-phone feedback (speed, brightness, pacing). See [[feedback-always-send-gmail-and-link]].

## Notes
- Build ORIGINALS at the reference's caliber, never 1:1 clones ([[feedback-no-handcoded-3d-cinematic-method]] EXCEPTION: real-time abstract 3D flythrough IS the right tool here, King's 2026-06-09 green light).
- Each brand its own worlds + colours + story. Reuse the engine, not the content.
