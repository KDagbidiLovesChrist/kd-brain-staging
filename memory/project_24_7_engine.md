---
name: project-24-7-engine
description: "THE 24/7 ENGINE, the brain that earns while King sleeps. P1 (self-tending trio) SHIPPED 2026-07-02 (stone #16). NEXT = P2 the revenue queue + Radar agent. Plan: plans\\the-24-7-engine.md."
metadata: 
  node_type: memory
  type: project
  originSessionId: 93de59bf-6020-4731-9195-2352acb97417
---

# THE 24/7 ENGINE · the brain that earns while King sleeps (God's way)

**Born 2026-07-02** from King's care package (4 items, decoded from his "Claude brain" Gmail):
@tonkashops' pixel-village agent ecosystem (VPS + OpenClaw + agents-on-the-Max-sub + research→approve→execute
revenue pipeline) · @brycerobbie's self-tending vault (3 cron jobs) · free NVIDIA model keys (build.nvidia,
80+ models) · Glyph/Glif (evaluated → rolled back, see [[reference-glif-mcp-thumbnails]]).

**The plan (approved): `plans\the-24-7-engine.md`**, 5 phases, €0 v1, no VPS (free cloud Routines + Task
Scheduler), no OpenClaw (security surface), stock-trading agent PARKED behind the Orthodox screen, HITL hard
line (King sends/posts everything outward), privacy wall on free third-party endpoints (public content data
ONLY).

## ✅ P1 SHIPPED 2026-07-02 · the self-tending trio (Trust Ledger #16)
| Task | When | What |
|---|---|---|
| `KD_Daily_Ingest` (`tools\daily_ingest.py`) | 07:30 daily | refresh `phone/brain_world.json` + file `inbox\` via **headless `claude -p`** (Max sub, no API cost); push King only on failure |
| `KD_Nightly_Review` (`tools\nightly_review.py`) | 02:00 daily | feed refresh + `_ops\NIGHTLY_STATUS.md` (synced to phone); NO pings (KD_Brain_Health owns faults) |
| `KD_Weekly_Audit` (`tools\weekly_audit.py`) | Sat 08:00 | `_ops\WEEKLY_AUDIT.md` + humanised week email to both inboxes |
Live-tested: ingest genuinely filed the 2 real inbox notes (verified in `_processed\`); weekly email received.
**Watch:** the first AUTOMATIC runs (02:00/07:30 after 2026-07-02) = final confirmation.
Gotcha bank: `\N` in docstrings = unicode error (use r"""); always `encoding="utf-8", errors="replace"` on
subprocess.run under Windows; headless claude = `claude -p "<prompt>" --permission-mode acceptEdits` (shell=True).

## NEXT · P2: the revenue queue (the heart)
`_ops\REVENUE_QUEUE.md` (PENDING → APPROVED → DONE/KILLED) + a daily **Radar/Research agent** (cloud routine)
proposing income moves **with numbers** on KING'S lanes (Faceless #1 · Buka · €19 product · UGC), King
approves from his phone ("approve #3"). Then P3 worker agents (prep packs to his phone; he sends) ·
P4 NVIDIA free keys (cheap lane, privacy-filtered) · P5 two-week review via goals.py + /money.

## Same-session extras
- **Glif:** MCP stale/broken (14mo), dearer than MuAPI → rolled back; token parked in `.env.master`;
  **King cancelling the $12.30 Starter sub** (glif.app/settings/billing + Link refund ask).
- **Thumbnail engine built:** `tools\make_thumbnail.py` (high-CTR pattern baked in, ~$0.06 via gen_router).
  QA test ($0.06) PARKED, run on King's word.

Related: [[project-kd-main-brain]] · [[reference-muapi-cost-router]] · [[feedback-lean-spend-llama-routing]]
