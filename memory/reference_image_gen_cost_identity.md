---
name: reference-image-gen-cost-identity
description: "Image-gen cost decision (tested 2026-06-28): FREE tools (Pollinations Flux/gptimage) make nice images but CANNOT hold King's blank-faced character identity (they add eyes / invent a new person). Use ~8c kie nano-banana for character-consistent shots, free tools for backgrounds/b-roll only. Free-at-scale = a local LoRA of the character."
metadata:
  node_type: memory
  type: reference
  originSessionId: 377b479b-4ca1-4b54-a7d6-e4d24f3654c3
---

# Image generation: cost vs character-identity (tested, not guessed)

King asked the right lean-spend question: "surely there are cheaper image tools." Tested it properly
on his actual character (2026-06-28) instead of asserting.

## The test result (data, 3 free models)
Fed the **locked 2D character** (blank faceless face, navy+gold braids, gold headphones, navy hoodie,
gold cross, gold halo) to **free Pollinations** image-to-image: models `flux`, `gptimage`, `flux-kontext`
(`kontext` 500s). **All FAILED to hold his identity**, every one gave him a **full face with eyes** and
basically invented a new person (a different anime guy, then a realistic woman). His core identity (the
**blank faceless face**) was lost every time. Free Flux is great at *fresh* images, weak at *locking an
existing subject*.
**kie nano-banana (~$0.08, Gemini edit model) DID hold his exact character**, it actually does
identity-preserving image-to-image. That ~8c is what you pay for.

## The rule (lean-spend, [[feedback-lean-spend-llama-routing]])
- **Character shots (identity must stay locked):** use **kie nano-banana (~$0.08)** via `gen_router.py`.
  A full 12-frame storyboard ≈ **$1**. Trivial; don't micro-optimise it.
- **Backgrounds / b-roll / generic stills (identity doesn't matter):** use the cheap/free tools,   **Flux Schnell** (fal.ai/Replicate ≈ $0.003, ~25x cheaper) or **free** Pollinations / Cloudflare
  Workers AI free tier. Save money HERE.
- **Free-at-scale endgame (when pumping out many videos):** train a small **LoRA of King's character**
  and run **local Stable Diffusion**, free forever after a one-time setup, needs a decent GPU. Check
  King's laptop can run it before committing to that path.

## Wiring note
`gen_router.py` currently floors at ~$0.08 for images (compares Gemini/MuAPI/kie nano-banana). The truly
cheap providers (Flux Schnell on fal.ai/Replicate, free Pollinations/Cloudflare) are **not wired in yet**
, add them for the background/b-roll lane when it's worth it. Verify CURRENT prices before wiring
(don't trust stale numbers). Don't route character shots to them (identity drift, proven above).

## Related
[[reference-muapi-cost-router]] · [[reference-faceless-moving-composite-engine]] ·
[[feedback-lean-spend-llama-routing]] · [[project-content-engine]]
