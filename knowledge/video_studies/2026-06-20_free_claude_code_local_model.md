# Video Study · Run Claude Code CLI for $0 with a local model (@emilsystems, TikTok)

**Source:** uploaded clip (TikTok @emilsystems) · Watched 2026-06-20 via `/watch`. Confidence 5/5.

## What it actually shows (the trick)
Point the **free Claude Code CLI** at a **free local model** instead of paid Claude:
1. Install **Ollama**; `ollama pull qwen2.5-coder`
2. `ANTHROPIC_BASE_URL=localhost` (redirect the CLI to the local model)
3. Use Claude Code as normal, tokens run on your laptop = **$0**.

## The honest truth (the video admits it)
- On-screen: *"good enough for solo coding on small projects, **but not for full agentic builds**."*
- A laptop local model (qwen2.5-coder) is **far weaker than Opus**. Same *interface*, NOT the same *brain*.
- This conflicts with KD's **"optimise what is best"** rule (Opus stays, because output = the product that earns).

## What it does NOT do · does NOT make other APIs free
- **Gemini API** (used by `/watch`, image gen): separate API. Already on a **generous free tier**. Local
  models can't reliably *watch video*, so this trick doesn't apply. Cost ≈ near-zero already.
- **Seedance / KIE.ai** (AI VIDEO for cinematic sites): **cannot be localized**, AI video generation needs
  big cloud GPUs. No free laptop equivalent exists. Already cheap (~$1.33/site). Spend only when a flagship/
  client needs it. The `ANTHROPIC_BASE_URL` trick is Anthropic-CLI-only; it has nothing to do with these.

## The SMART application (matches today's GLM 5.2 routing)
The real win isn't "everything free", it's a **cheap GRUNT LANE**:
- Point Claude Code at a cheap model **for bulk/simple/non-client tasks**, either local Ollama ($0) OR
  **GLM 5.2 via OpenRouter** (~5× cheaper, much stronger than a laptop model). See
  `memory/feedback_lean_spend_llama_routing.md`.
- **Keep Opus (me) for money/client/complex work**, never cheap out on the work that sells.
- Gemini = stay on free tier. Seedance = pay-per-use only when it earns.

## DO
Optional setup (on King's laptop): a cheap-lane profile for grunt coding. NOT the default. King's call +
needs an OpenRouter key (GLM) or Ollama installed (already has Ollama). Don't route earning work to it.
