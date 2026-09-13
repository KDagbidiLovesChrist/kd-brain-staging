---
name: reference-androo-live-cockpit
description: The androo-style BEAUTIFUL-AND-LIVE brain cockpit target + the real Mission Control engine built + the money-engine fault to fix
metadata: 
  node_type: memory
  type: reference
  originSessionId: a2189eca-f505-4a75-9e3c-7a72a441e817
---

# The androo Live Cockpit — EDEN LIVE (BUILT 2026-07-05) + the money-engine fault

## ✅ THE MARRIAGE IS BUILT · EDEN LIVE
`http://127.0.0.1:5055` now serves **EDEN LIVE**: the approved Eden garden look driven 100% by the real Mission Control engine (5s poll of `/api/status`). Files: `_ops/eden_live.html` + `_ops/eden_live.js` (new, template untouched) + additive routes in `tools/mission_control.py` (`/` = EDEN LIVE, `/classic` = old dashboard, whitelisted art routes, `extras` stones/lessons in the API). **Auto-starts at login** via `tools/start_mission_control.bat` + Startup `KD Mission Control.lnk` (voice-server pattern).
- The 19 REAL automations are the workers: status-colored dots per realm (money→M, brain→C, infra→W; F/T contemplative with real stones/lessons counts), realm rings + storm glow on failures, red "N need attention" chip, honest feed, offline "the garden sleeps" veil.
- **Living choreography (King asked 07-05, all real-status-driven):** map: ok = orbit + offering trips to the Tree, running = racing ⚡, failed = frozen red ✗ SOS, stale = 💤 drift; summons = golden beam from the Source + burst + bubble + feed announce ("⚡ called to work" / "✓ finished the labor" / "✗ fell at its post"); roaming narration bubbles on map AND in scenes. **Scenes: WALKING 🤖 robot characters** (v4, after King said "the dots are not moving"): healthy bots patrol paths with a gait animation (proven 9-17% movement in 4s), summoned bots march to the forge and hammer with sparks, fallen bots lie tipped sideways flashing red (0.0% movement, honest), sleeping bots breathe with 💤. A summoned machine joins the scene cast (worst-6 re-forms).
- **⚠ CACHE LESSON (07-05):** King saw a STALE cached page ("dots not moving", old v1 JS) → server now sends `Cache-Control: no-store` for `/`, `/classic`, and all .js/.html (after_request in mission_control.py). Bump `?v=` on eden_live.js when editing anyway. Any served UI must be cache-proofed BEFORE showing King.
- **⚠ CLASS-COLLISION LESSON (07-05, cost ~2h of debugging):** a pale "ghost panel" behind every scene robot was NOT sprites/compositing/caching, it was the robot wrapper div named `bot` colliding with the Eden template's `.bot` selector (the bottom HUD bar, cream gradient). Renamed to `.robo`. Rule: before adding a class to eden_live.html, grep the CSS for the name (`.top`/`.bot`/`.d`/`.e`/`.nm`/`.cnt` are all taken by the template). Robots use v6 sprites: bot_walk/bot_orb/bot_down + pre-flipped `_l` variants (all whitelisted in mission_control.py).
- **📦 VISIBLE DATA FLOW (v5, King asked 07-05):** applied the brain's own LOGOS-OS consensus pattern (bezier packet edges). Healthy workers make constant pilgrimages realm→Tree→back on curved paths (QA: up to 6 travelers at once). When a scheduled task's REAL last-run changes, a **labeled golden packet** rides the curve ("📦 Lead Pinger · lead pings", CARGO map in eden_live.js), the Tree flares on arrival, the feed announces the delivery. Ambient pilgrimages carry NO label (nothing fake looks like data). Proven by firing KD_Lead_Pinger via real Task Scheduler.
- **💡 SELLABLE:** King wants to build living-ecosystem cockpits for other money engines and SELL them → filed in `knowledge/ideas_backlog.md` (Living Ecosystem Cockpits as a PRODUCT).
- Realm scene = control room: pills + panel rows with real notes, Run buttons (gold HITL confirm modal for outward jobs), live logs drawers.
- Fictional household KEPT as decor at King's request, clearly separated (dimmed, dashed, "of the household", never status-colored).
- QA passed 2026-07-05 (Playwright, 0 console errors): summons/finish announces, HITL cancel, logs streaming, context_check exit 0, /classic intact, veil works, non-whitelisted paths 404.

## 🌆 THEME TWO · the CARBON-COPY CITY (King approved the A+B mix, 2026-07-06)
Captured androo's ACTUAL TikTok frames at last (Playwright HEADED to the video URL works; headless research could not). His look = dark pixel motherboard-city, neon sectors, trace roads. Built as a switchable theme: `_ops/eden_theme.js` (33 lines, themes registry + toggle btn + per-theme CENTER + trip-curve recompute) + `body.city` dark terminal skin in eden_live.html + art `_ops/city_map.png` (5 neon pentagon sectors in realm colors + blazing Source core, aligned to REALMPOS) + `city_{C,W,M,F,T}.png` sector scenes (server cathedral / relay yard / golden vault / rose sanctuary / summit spire). Toggle ⚡CITY / 🌿GARDEN next to TOUR, persisted in localStorage. Same live engine, only the skin changes; white-gold robots kept (King's call). QA 07-06: toggle clean both ways, 0 errors. The sellable product now has TWO themes (garden / cyber-city).

## The target (context)
@androoagi's TikTok *"AI Agent Environment Tour #openclaw #ai"*: **BEAUTIFUL AND LIVE at the same time.** The old trap was delivering one at a time (pretty-fake Eden vs real-ugly dashboard). Closest verified public analog: OpenClaw Office (github.com/openclaw-office/openclaw-office) — live isometric agents with speech-bubble logs. The actual TikTok frames remain unverified (unfetchable); King's eyes are the final reference.

## The engine (unchanged core)
`tools/mission_control.py` — Flask `127.0.0.1:5055`, reads live Task Scheduler (KD_* tasks) + logs + state → true status ok|stale|failed|running|idle; POST `/api/run/<id>` (outward needs `{"confirm":true}`); `/api/logs/<id>`. Static EDEN.html/eden_template.html/build_eden.py still work for the Vercel deploy (separate lifecycle).

## 🔴 The money-engine fault (fix first — found live by the cockpit)
Four money automations FAILING since 2026-07-03 (code 2147946720, logs cold), Task Scheduler shows fake-green: **KD_Revenue_Radar · KD_Daily_Ingest · KD_Daily_Client_Scan · KD_Weekly_Audit**. Reproduce/fix: run each `python tools/<name>.py` from the brain root, read the real error, fix root cause. This directly starves the first-euro mission.

## Pipeline facts (for wiring)
14 scheduled KD_* tasks; ~25 runnable automations (money/brain/infra/content); true status = Task Scheduler + logs (`~/.kd_brain_sync.log`, `_ops/logs/*.log`) + state (`_ops/.brain_health.json`, `_ops/REVENUE_QUEUE.md`, `_datacentre/dcim.json`). Existing voice Flask server `tools/voice/voice_aide_api.py` (port 5000) could also host it. See [[project_24_7_engine]].
