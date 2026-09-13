# MuAPI + the cost-based generation router (pick the cheapest tool per job)

**Added 2026-06-26.** King sent a TikTok (@nathanhodgson.ai) about "Open Generative AI" → it's a
front-end over **MuAPI (muapi.ai)**, a unified "one key, 200+ models" gen-AI gateway (Seedance, Kling,
Veo, Flux, Nano Banana, Sora, Suno, etc.). King's instruction: **wire it in and, when choosing a tool,
choose by cost.** Done.

## What's wired (3 providers: Gemini/Veo · MuAPI · kie.ai)
- **Keys in `C:\Users\Dell\.env.master`:** `MUAPI_API_KEY` (verified HTTP 200, acct kingagbidi@gmail.com) ·
  `GEMINI_API_KEY` (already there, used for Veo + Gemini image).
- **`tools\gen_router.py`**, THE "which tool?" brain. `quote` (free) ranks **Gemini/Veo + MuAPI (live
  `estimate-cost`) + kie.ai** by real USD cost; `image`/`video` run the cheapest via the proven generators,
  with **cost-ordered fallback**, if the cheapest fails (e.g. Veo billing off) it drops to the next cheapest
  automatically (failed attempts aren't charged, so fallback is free). Tiers: `budget` (Seedance Pro / Veo Lite)
  · `balanced` (Veo Fast) · `premium` (Seedance 2.0 / Veo / kie) · `any`=cheapest.
- **`tools\batch_seedance.py`**, now routes EVERY image+video through `gen_router.py` (TIER knob at top).
- **`tools\muapi_generate.py`**, MuAPI client (`image`/`video`/`estimate`); base `https://api.muapi.ai/api/v1`,
  auth `x-api-key`. Result is in `outputs[]`; request echoed in `inputs` (parser skips `inputs`, reads `outputs`).
- **`tools\gemini_video.py`**, Veo 3.1 via google-genai (`lite`/`fast`/`quality`); durations snap to 4/6/8s.
- **`tools\gemini_image.py`** (existing), Gemini Nano Banana image; dispatched by the router.
- Wired into **`commands\seedance-site.md`** ("Cost-aware generation" + Steps 1, 2) and **`commands\video.md`** (Build step).

## Verified costs (2026-06-26, live) · cheapest in bold
| Job | Gemini/Veo | MuAPI | kie.ai |
|---|---|---|---|
| Image 1k | $0.067 | **$0.06** | $0.08 |
| Image 2k | $0.101 | $0.09 | **$0.08** |
| Video 720p/5s i2v | **Veo Lite $0.30** (/6s) | Seedance Pro $0.36 | $1.03 |
| Video 1080p/5s i2v | **Veo Lite $0.48** (/6s) | Seedance Pro $0.62 · SD2 $1.25 | $2.55 |
| Video premium 1080p | Veo Quality $2.40 | **Seedance 2.0 $1.25** | $2.55 |

**Winner pattern:** VIDEO → **Gemini Veo 3.1 Lite** (King's cost pick, confirmed by the router) · cheap premium
video → MuAPI Seedance 2.0 · IMAGE → MuAPI/Gemini neck-and-neck (~$0.06, 0.07). Net seedance-site ≈ **$0.55, 0.60**
vs old ~$1.33 → well under half. (Veo durations snap to 4/6/8s, so 5s → 6s.)

## Status / honest flags
1. **MuAPI: LIVE-TESTED OK.** Generated a real Nano Banana image ($0.06) + Seedance Pro i2v 720p clip ($0.36,
   14.8MB mp4, QA'd good). Balance was topped to $10 (King). **Bug found + fixed:** result is in `outputs[]`,
   request echoed in `inputs`, parser now skips `inputs`. MuAPI has no free API credits; top-ups via `/money`.
2. **Veo: built, not yet live-run.** `gemini_video.py` follows Google's documented API; confirm on first run.
   **Veo needs the Gemini API PAID tier enabled** (not on free tier), verify billing on King's Gemini project
   before relying on it for production. Image + watch may run on free tier; Veo will not.
3. MuAPI request schemas (verified via OpenAPI): `seedance-pro-i2v` {prompt, image_url, resolution, duration} ·
   `seedance-pro-t2v` {prompt, aspect_ratio, resolution, duration} · `seedance-2-image-to-video` {prompt,
   images_list[], aspect_ratio, duration} · `nano-banana-2` {prompt, aspect_ratio, resolution, output_format}.
   Veo: `veo-3.1-{lite,fast,}-generate-preview`, config {resolution 720p/1080p/4k, durationSeconds "4"/"6"/"8"}.

## NEXT
Optional live Veo test once Gemini paid-tier billing is confirmed (one Veo Lite clip ~$0.30) → then make the
router the default in `batch_seedance.py` too. Log MuAPI/Veo spend via `/money`.
Related: [[skill_seedance_animated_websites]] · [[feedback_lean_spend_llama_routing]] · [[project_accountant_finances]]
