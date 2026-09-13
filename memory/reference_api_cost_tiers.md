---
name: reference-api-cost-tiers
description: "Cost-tiered routing for every API/tool (FREE -> CHEAP -> PREMIUM). King's rule: tier tools and pick by task - free/cheap for testing + iteration, premium only for the final client-facing deliverable."
metadata: 
  node_type: memory
  type: reference
  originSessionId: e7f03826-5818-437b-983c-47c672a31639
---

King's standing rule (2026-06-09): **every capability should have cost tiers**, and we pick the tier by the job. Use FREE/CHEAP for testing, drafts, backgrounds, iteration; spend PREMIUM only on the final hero/client-facing output. Extends [[feedback-lean-spend-llama-routing]]. King enters all payment; keys live in `.env.master` only.

## The tier table (pick the lowest tier that meets the task)

| Capability | FREE (€0) | CHEAP (~cents) | PREMIUM |
|---|---|---|---|
| **Image gen** | Google ImageFX / Bing DALL·E 3 (manual, King generates + sends, like the ref video) · Cloudflare Workers AI FLUX-schnell (free token) | **Gemini flash-image** (`tools\gemini_image.py`, billed key, ~cents) | Gemini **pro-image** (`gemini-3-pro-image`, sharper, can 503-busy) · Seedance stills (KIE) |
| **Video gen** | **Real-time 3D = no gen at all** (Three.js, the LUMO/AUREO/hero engines) · Luma Dream Machine / Kling / Hailuo / Pika free daily (manual, King sends) | Seedance via KIE (~$1-2/clip) | Veo (Google) · Runway · Kling Pro |
| **LLM reasoning** | Ollama local (Llama/Mistral) | Claude **Haiku** · Gemini flash | Claude **Opus** · Gemini pro |
| **Voice / TTS** | edge-tts (free) | · | ElevenLabs (`.env.master`) |
| **Web search** | Brave MCP · DuckDuckGo | · | Perplexity ($50 credit) |
| **Scraping** | Firecrawl free · plain requests | Apify cheerio-scraper ($5/mo credit) | Apify web-scraper + residential proxies |

## Convention
- Tag the task: **[TEST]** -> free/cheap only; **[FINAL]** -> premium allowed.
- Backgrounds, textures, drafts, experiments = FREE/CHEAP. The hero/client deliverable = best tier.
- Default to **real-time 3D** for motion (free) before reaching for paid video.

## Hard-won lessons (2026-06-09)
- **Gemini free tier = image limit 0** (text works, images 429 "limit: 0"). Image gen needs a **billed** project. A key is tied to a project; billing must be on THAT project. New key format starts `AQ.` (not `AIza`).
- **Pollinations.ai is no longer free** - the no-key endpoint now returns an `x402` payment-required JSON, not an image.
- **gemini-3-pro-image** often returns **503 "high demand"** - retry with backoff or fall back to `gemini-3.1-flash-image` (already great quality).
- Screenshots of API keys are unreliable (capital-I vs lowercase-l look identical) - always get the key **pasted as text**.
- Truly-free no-signup image APIs are mostly gone; the reliable €0 path is **King generates on a free web tool and sends the file**, or a **free Cloudflare/HF token** for programmatic gen.
