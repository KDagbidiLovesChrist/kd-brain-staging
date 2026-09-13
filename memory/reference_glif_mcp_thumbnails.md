---
name: reference-glif-mcp-thumbnails
description: "Glyph = the Glif MCP (glif.app). Evaluated 2026-07-02: MuAPI beats it on cost; the official MCP server is stale/broken vs glif.app's new API. Token parked in .env.master. Thumbnails = our own MuAPI engine instead."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 93de59bf-6020-4731-9195-2352acb97417
---

# Glyph (Glif MCP) · evaluated, rolled back, lesson banked (2026-07-02)

**What it is:** "Glyph" = the **Glif MCP server** (`@glifxyz/glif-mcp-server`), glif.app's connector that lets
Claude run community AI workflows (image/video/thumbnail generators) as tools, with prompts auto-optimised
inside each "glif".

## The cost head-to-head (real numbers, no spend needed)
Glif = ~$0.01/credit (200 for $1.99-1,000 for $9.99-10 FREE credits/day, don't roll over).
| Job | Our MuAPI (live-verified) | Glif | Winner |
|---|---|---|---|
| Quality image | $0.06 | ~$0.10 (Flux Ultra 9.97 cr) | MuAPI |
| Video 720p | $0.30 (Veo Lite) | ~$0.50 to $1.00 (50-100+ cr) | MuAPI |
| Premium video | $1.25 (Seedance 2.0) | ~$1.00+ | tie-ish |
**Verdict: MuAPI stays the engine.** Glif's only edges were the free daily credits + prebuilt thumbnail glifs.

## The live test that killed it (why it's parked, not adopted)
- King made a free account + token. Token stored safely (never in a tracked file).
- The MCP server boots (v0.9.9) BUT its discovery call (`/api/glifs`) gets an HTML error page back,   **glif.app overhauled their API** (their old simple-api literally answers "This API has been deprecated")
  and the MCP package was **last published 2025-04-23 (14+ months stale)**.
- Per "nothing is done until proven working": rolled back. `settings.local.json` deleted; no trace in the repo.

**Why:** don't wire half-dead connectors into the brain; test before trusting; €0 spent finding out.

**How to apply:**
- `GLIF_API_TOKEN` is **parked in `.env.master`** (annotated). Re-check ONLY if glifxyz ships an updated
  MCP server (`npm view @glifxyz/glif-mcp-server time.modified` newer than 2025-04), then re-test discovery
  before trusting.
- **Thumbnails = our own engine on MuAPI** (~$0.06 each, cheaper than Glif anyway): `tools\make_thumbnail.py`
  via [[reference-muapi-cost-router]].
- Config security pattern that made this safe: `settings.json` is git-TRACKED (syncs to phone), secrets go in
  **`settings.local.json`** (confirmed git-ignored) or `.env.master`, never settings.json.

## ⚠️ Subscription status (checked in Gmail 2026-07-02 23:30)
**NOT cancelled yet.** Receipts show a **Glif Starter subscription CONFIRMED + CHARGED $12.30 (€11.17) on
2026-07-02 14:20** (Link/Stripe, Visa ••••9424, receipt 2708-8023). No cancellation email exists.
**King's hand:** glif.app/settings/billing → cancel, so the next month never bills. Update this section when
the cancellation-confirmed email lands. `/money` note: one-off €11.17 already spent; recurring unless cancelled.

Related: [[reference-muapi-cost-router]] · [[feedback-lean-spend-llama-routing]] · [[project-faceless-content-engine]]
