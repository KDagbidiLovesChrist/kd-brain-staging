---
name: project-flagship-rebuild
description: "Redo ALL of King's website flagships + portfolio to top-tier ONLY (real 3D / Seedance / animated, NO 2D templates). Locked process: research each -> design -> King confirms FINAL before prod. Started 2026-07-10; SERA exemplar built."
metadata: 
  node_type: memory
  type: project
  originSessionId: 38f384dd-1b21-443a-90ab-197c36cea65a
---

# Flagship Rebuild · top-tier only (2026-07-10)

King's call (2026-07-10): the 146 volume demos + old portfolio read as "bad", because they are 2 templates recoloured, not bespoke. **REDO everything to flagship level: only the best, real 3D + Seedance (scroll-scrub AI video) + animated. NO 2D templates.** Quality over quantity, 3 jaw-dropping pieces beat 146 recolours. Each flagship its OWN unique world (never King's personal navy/gold, [[feedback-palette-personal-only]]).

## The LOCKED process, per flagship (King's rule, 2026-07-10)
1. **Research** the best-in-class references for that vertical (reference-driven, model the winner, [[feedback-reference-driven-design]]).
2. **Design** it, unique, top-tier.
3. **Show King** the visual (Rule 18).
4. **King confirms the FINAL design** (Rule 21: Approval before Production).
5. **ONLY THEN deploy to prod.** Nothing reaches production without King's explicit final-design yes.

## Exemplar built: SERA (design house)
`_ops/FLAGSHIP_sera.html`, espresso + ivory + copper, Cormorant serif, real-time Three.js torus-knot hero + GSAP reveals + mouse parallax. Free (Three.js + GSAP via CDN; ADD SRI hashes + self-host or pin for prod, security). Sets the quality bar. Pending: reference research to sharpen + King's final confirm.

## 🏆 CORNERSTONE (2026-07-11) — the REAL direction, King's "top 3D flagship" demand
King rejected Prototype A ("this is terrible, we are talking top 3d flagship... top tier research and logic and planning"). Ran the full ultracode workflow: 11 agents (4 research lanes: top-3D tech / teardowns / King's own engines / mobile perf → 3 independent concepts → 3 adversarial judges → locked spec). **WINNER: CORNERSTONE — The Living Monolith, 52/60** (wow 9 · originality 9 · brand fit 10) vs FIAT LUX 49.5 vs SOLAS 45.7. One rough stone; the visitor's first scroll strikes the First Cut; 7 cuts reveal the 7 real flagships playing INSIDE the stone as ore veins (per-flagship rim treatments); interior = service SKUs; climax = the dust writes IT WILL BE DONE then engraves it; finale = all dust streams into the Book-a-call button. Grafts from losers folded in (dock fast-lane, thumb bar, FLIP CTA, inflow, motto-by-the-world).
- **LOCKED SPEC: `_ops\CORNERSTONE_SPEC.md`** (build order M1-M7 with jaw-drop gates; 8 pre-cut Blender states, NO runtime CSG; one 65k GPGPU particle organism reused everywhere; mobile tiers; €0).
- **VISUAL BOARD (Rule 18): `Documents\Website Builder\kd-site-v3\cornerstone-board.html`** — 9 CSS-crafted frames w/ real loops embedded, consensus scores. Live preview: `kd-site-v3-nx8t0rwp7-king-david-s-projects2.vercel.app/cornerstone-board.html` (verified 200, public).
- **⚠️ LESSON (King, 2026-07-11): "the 3d looks poor quality"** — he judged the board's flat CSS sketch frames as the 3D. CSS sketches answer STRUCTURE, never LOOK. For any 3D build: show REAL renders only. He ordered: plan 0→100, start from basic, build up.
- **THE LADDER: `_ops\CORNERSTONE_BUILD_LADDER.md`** — 10 stages 0→100, each built REAL, each gated on King's eyeball of a real render. No sketches ever again for look decisions.
- **STAGE 0+1 BUILT REAL: `cornerstone-m0.html`** — actual Three.js: noise-sculpted standing stone (icosahedron detail-80, CPU simplex fbm+ridge, tapered), MeshStandard basalt + gold env (assets/env_gold.png PMREM), GLSL simplex ore-vein emissive (ridged bands × cluster mask, pulsing) injected via onBeforeCompile, fresnel backside halo shell, warm backlight glow disc, 5.2k dust points, bloom 0.5 + grain/vignette, breathing + camera drift + mouse parallax. Self-QA'd via headless render (v1 → composition fix → v2 GOOD). Preview: `kd-site-v3-mzcgffcra-king-david-s-projects2.vercel.app/cornerstone-m0.html` (200, public).
- **🛑 ALL HUB BUILDING PAUSED (2026-07-11, King's call): vision-first discovery NOW.** After 3 rejected builds in ONE session (hub-A page, CORNERSTONE stone, alive-direction) King named the root cause: building on guesses. He wants the **"My Notion Systems" (TikTok) planning mindset: understand EXACTLY what he wants, plan the project properly, THEN storyboard, THEN build.** The living plan = [[project-hub-vision]] (`memory\project_hub_vision.md`) — fill top-down, nothing builds until Vision + References + Non-negotiables locked. `hub-alive.html` was built (living dust + micro-worlds + strike + sound) but is PARKED UNSHOWN pending discovery. LESSON FOR EVERY FUTURE BUILD: discovery answers first, storyboard second, build third — never reversed, no matter how fast building feels.
- **⏸ CORNERSTONE PARKED (2026-07-11, King's call):** saw the real Stage-1 stone render and said "I don't like how the website looks... I like how it IS already, maybe we make it more cooler and more life." **DIRECTION LOCKED: keep the CURRENT live hub concept (KD dust journey + worlds + golden hand) and ENHANCE it — cooler + more alive.** No rebuild. The stone (cornerstone-m0.html), spec + ladder stay banked as a possible future flagship demo for a CLIENT vertical, not King's hub. hub-A.html stays as parts-bin. The v1/v2 elite-kit + moving-cards work (index-elite.html) is directly reusable: it IS "current site, more alive."

## 🟢 HUB REDO IN PROGRESS (2026-07-11) — awaiting King's final-design yes
Phase A (kingdavidagbidi.com / kd-site-v3) built on a COPY, engine 100% untouched.
- **File:** `Documents\Website Builder\kd-site-v3\index-elite.html` (copy of index.html + elite kit). Promote to index.html + deploy prod ONLY on King's explicit yes.
- **v1 elite kit:** custom gold cursor (lerped, swells over interactives, screen-blend), magnetic hover (CTAs/nav/cards), momentum smooth-scroll (desktop wheel; touch native), staggered per-beat reveals, card thumb Ken-Burns. All desktop-gated (`if(!fine)return`); mobile keeps native. QA: 0 console errors desktop+mobile, all interactions verified via Playwright.
- **v2 real-footage card loops (King's pick 2026-07-11: "free real-footage loops and lemme see ai loops"):** screen-recorded all 7 LIVE flagships via the MCP Playwright `browser_run_code_unsafe` recordVideo trick (no install; scripted easeInOut scroll 0→72% over 9s), ffmpeg ping-pong seamless loops 640x360, in `assets\loops\<name>.mp4`+`.jpg` (~1.9MB total for 7). Cards = `<video muted loop playsinline preload=none poster=loops/x.jpg>`; a MutationObserver on #b-work.active plays them only while the Work beat is active + desktop-only (mobile shows posters, preload=none = no data). QA: 7 play on active, 7 pause off-screen, 0 errors, mobile clean.
- **AI loops:** NOT generated (lean-spend, Rule 12) — real-footage wins for a portfolio (shows real work). Offered to gen 1-2 samples (~€0.60-1.20 via gen_router) on King's word. LUMO loop = least punchy (caught bright intro); can resample its morphing worlds.
- **Live PREVIEWS (public, Vercel protection turned OFF on project via API — ssoProtection=null; domain untouched):** v1 static = `kd-site-v3-63izz3wpf-king-david-s-projects2.vercel.app/index-elite.html` · **v2 moving = `kd-site-v3-bgwebonok-king-david-s-projects2.vercel.app/index-elite.html`**.
- **Raw captures** parked in scratch `kd_rawvid` (mv blocked by browser lock → left in `assets\_rawvid`, excluded via `.vercelignore`).
- **⏳ WAITING ON KING (2026-07-11):** he had NOT opened the preview; reacted "the hub looks exact same?" (he pictured it from my words). KEY: cursor+magnetic are desktop-only, so on phone the change reads as small. Made a **19s demo video** (Playwright recordVideo driving the mouse → ffmpeg mp4, 720p 7MB) showing cursor swell + magnetic + smooth scroll + moving cards. Live tappable: **`kd-site-v3-ft0xw77x4-king-david-s-projects2.vercel.app/elite-demo.mp4`** (plays inline on phone). **OPEN FORK for King:** (A) "that's it" = polished-concept is right → harden + ship; OR (B) "want a new look" = he wanted a bigger VISUAL redesign (fresh concept, not the same hero polished) → research fresh refs + redesign hub from scratch. He replied "haven't watched it yet" → awaiting his watch + verdict. **Do NOT ship or redesign until he picks.** (Remove `elite-demo.mp4` from the folder before any prod deploy — it's just his preview.)
- **ON KING'S YES (ship path):** copy index-elite.html → index.html · `vercel --prod --yes` → `vercel alias set <url> kingdavidagbidi.com` + www · verify 200/0err/60fps/mobile · HARDEN: SRI hashes / self-host Three.js+GSAP, add `-webkit-backdrop-filter` (Safari, line ~74 .tier), delete elite-demo.mp4. Then Phase B client flagships.

## Then cascade (only after each is confirmed)
Rebuild the hub flagships (kingdavidagbidi.com, kd-site-v3), the portfolio, and the Upwork / buyer-facing samples around the new top-tier flagships. The old 2D template demos (kd-demos, 146 recolours) are retired from the pitch.

## Stack (Rule 25)
`/seedance-site` + `/immersive-site` + `frontend-design` + [[reference-photoreal-flagship-method]] + [[reference-ultra-realtime-3d-method]] + [[reference-lived-in-city-engine]]. Free-first (a Seedance AI-video hero is ~$0.60 via `gen_router.py`, optional). Serves King's first euro via a top-tier portfolio + Upwork.
