# Video Study · "Anime Content Factory with Claude" (TikTok @dubibubiii)

- **Source:** uploaded TikTok clip (68s, 9:16). Creator: `@dubibubiii`.
- **Watched:** 2026-06-23. **Method (honest):** Gemini `/watch` could NOT run in the web session
  (no `GEMINI_API_KEY`, King's "keys off the cloud" rule; local Whisper blocked by the network policy).
  Instead I extracted 9 frames with PyAV and read them with vision. The video's **on-screen text panels
  carry the full method**, so the substance is captured. **Caveat:** I read the burned-in captions +
  panels; I did NOT hear the spoken audio. Lesson below is built from what is verifiably on screen.

---

## THE OBJECTIVE LESSON (one line)
Claude can be the brain of an **automated "anime content factory"**, one pipeline that mass-produces
faceless anime channels (AI voices + AI music + AI visuals), and you can **sell that build to clients
for $3k, $5k+** on value, not hours.

## What he says Claude can do (verbatim from the on-screen panels)
**1. "What the Factory Actually Produces", three automated content types, one pipeline:**
- **Anime story shorts**, 8, 15 min episodes with AI characters, AI voiceover, AI music.
- **Lofi anime channels**, 8-hour study streams, looping visuals, background music.
- **Anime OST channels**, AI-generated soundtracks uploaded as "official" channel music.
- *"Each type monetizes differently. Together they hit $8,000+/month. One pipeline builds all three."*

**2. Voice system (ElevenLabs), the most concrete, copyable part:**
- Casting: **Kaito (main): Adam**, young, intense, slight edge · **Narrator: Antoni**, deep, cinematic,
  authoritative · **Female lead: Bella**, warm but with mystery.
- Settings: **Stability 0.35 · Similarity 0.85 · Style exaggeration 0.40 · Speaker boost ON.**
- Directing-prompt style (example shown): *"Read this line with urgency and quiet fear, like you just
  discovered something you weren't supposed to see… 'These files… they've been watching us for years.'
  Pause 0.8s after 'files.' Barely above a whisper on the last four words."*

**3. Pricing framework:**
- Price on **value delivered, not hours.** Automation saving 10 hrs/wk @ $75/hr = **$3,000/mo in value**.
- Charge **$3,000, $5,000 one-time** for the build (no-brainer ROI, client pays once, saves forever).
- Complex builds (multi-agent systems, custom MCP servers, cross-platform) → **charge more** (panel cut
  off mid-number; "a thousand" caption implies higher, ~$5k+ tier).

## Substantiated vs hype (honest)
- **Substantiated / doable today:** the voice-direction system (exact ElevenLabs settings + emotional
  prompts), the script/episode generation, the pipeline design, and the value-based pricing, all pure
  Claude reasoning + an ElevenLabs key. This maps 1:1 onto KD's existing `make-a-video` / `short-form-video`
  engines.
- **Needs money/tools:** consistent AI **characters** across episodes (image model + style lock), AI
  **music/OST** (Suno/Udio etc.), and **render/upload** at scale. These need keys + the laptop.
- **Hype to discount:** the "$8,000+/month while you sleep" number is the creator's claim, unproven, and
  YouTube monetization on faceless AI anime is policy-risky (reused content, OST "official" channels can
  hit copyright/authenticity flags). Treat the income figure as marketing, not a forecast.

## What it means for KD
- This is **not new**, it's a *niche skin* (anime) of what KD already does. It slots directly into the
  **MUM project** (done-for-you faceless AI viral channel) and the existing video engines. No new
  foundation, no Skill-Forge stop-and-talk needed.
- The genuinely valuable takeaways to **adopt**: (a) the **voice-direction discipline** (cast + fixed
  settings + per-line emotional prompts), add it to `short-form-video`/`make-a-video` intake; (b) the
  **value-based pricing line** ($3, 5k/build) for selling content automations to clients.

## What to DO
1. ✅ Demonstration produced (Claude doing exactly what he claims) → `2026-06-23_anime-factory-DEMO.md`.
2. Fold the voice-casting + settings + directing-prompt pattern into the video engines' intake checklists.
3. If King wants the *full* factory: run it as a niche of the **MUM faceless-channel** build, render
   step happens at the laptop (ElevenLabs + image/music keys), Claude does scripts/voice-direction/pipeline.
