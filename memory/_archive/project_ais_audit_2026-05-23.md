---
name: project-ais-audit-2026-05-23
description: "Full AIS audit session 2026-05-23, 12 transcripts extracted, Loom pipeline built, Obsidian fully populated, WAT origin corrected"
metadata: 
  node_type: memory
  type: project
  originSessionId: 4fcb1053-170e-46a5-9b5b-1551fb923af0
---

# AIS Audit · 2026-05-23 Session

**Status:** COMPLETE for highest-leverage content. Deferred: 700+ remaining modules + 1,300+ historical posts + YouTube Business Talks (lazy-load gap).

## What got extracted (location: `knowledge\ais_resources\transcripts\`)

**Loom transcripts (9, full Whisper-transcribed):**
- WAT Framework (AIS+ Claude Code 1.3)
- Token Management (AIS+ Claude Code 1.10), 5 prompting patterns + Context Rot framework + 5 token-saving strategies
- 7× AIS+ Build Portfolio Phase 3 (Intro, Time Lens, Income Lens, SOP Audit, Scoring Before Mapping ICE, Live Blueprint, Charge for Opp Map)

**Fireflies meeting notes (2):**
- TrueHorizon $211k Deal Part 2 (Project Management)
- TrueHorizon $211k Deal Part 3 (Modern Sales Pipeline)

**Fathom transcript (1):**
- TrueHorizon $211k Deal Part 1 (Scoping & Discovery), 59KB

**Build Your AI OS course (9 lessons text):** Full course bodies, King David has access, no Level 3 grind needed.

**Course inventories:** 10 AIS+ + 17 AIS-free courses module-tree mapped via `__NEXT_DATA__` (saved in `AIS_Audit\audit_log\`)

## Tools installed this session
- yt-dlp + faster-whisper + imageio-ffmpeg (Loom + Fathom transcript pipeline)
- `tools\transcript_extractor\loom_transcript.py`, handles Loom + Fathom URLs
- Token Dashboard (Nate Herk's local Claude Code analytics tool)
- youtube-transcript-api (Python package)
- n8n-mcp added to settings.json (needs Claude Code restart to activate)

## Obsidian vault populated
- 16 files pushed to `AIS Learnings/` (205KB)
- Master audit index: `AIS Learnings/_AIS_AUDIT_INDEX_2026-05-23.md`
- Token Management pattern: `Patterns/AIS_Token_Management_5_Patterns_and_Context_Rot.md`

## Confirmed corrections
- **WAT framework = Nate Herk's invention**, not King David's. Confirmed by transcript quote ("We use the WAT framework, where W stands for workflows, A stands for agent, and T stands for tools"). Fixed in CLAUDE.md + `reference_wat_framework.md`.

## Glaido signed up (King David did it 2026-05-23)
- Free tier confirmed
- Pending: install browser extension / desktop app for daily voice use

## KIE_AI key · PENDING
- King David signed up (kingagbidi@gmail.com)
- API key visible at https://kie.ai/api-key but masked (starts with `a9cd2844...`)
- TODO: King David copies full key + adds line to `C:\Users\Dell\.claude\.env`: `KIE_AI_API_KEY=...`

## Tools recommended (NOT installed · King David's call)
| Tool | Why | Free? |
|---|---|---|
| ClickUp | TrueHorizon $211k deal + Luca's auto-detailing used it (6-category board) | ✅ |
| Cal.com | Booking automation for plumber niche / second client | ✅ |
| Resend | Transactional email (better than Gmail SMTP for clients) | ✅ |

## Deferred for next AIS audit session
- 700+ remaining Loom transcripts (curated list of ~88 priority ready, URL extraction not done)
- 16+ YouTube Business Talks (lazy-load gap, need click-to-load pattern)
- 1,300+ historical Nate posts (pages 2-67)
- TrueHorizon Discovery Call SOP (empty body, special handling)

## How to apply
- Read `knowledge\ais_resources\transcripts\` for full transcripts when working on any related skill
- Read `knowledge\ais_all_learnings.md` (779 lines) for compiled findings + tool recommendations
- Read `AIS_Audit\audit_log\to_install.md` for the install/decision punch list
- All linked in Obsidian under `AIS Learnings/_AIS_AUDIT_INDEX_2026-05-23.md`

---

## 2026-06-21 UPDATE · harvested backlog DRAINED
King: "drain the 8 pending." Reality: the 8 "pending" in `loom_full_extraction.tsv` were a **stale
index**, all already transcribed in prior sessions (disk has **128 transcripts** now). Only 1 was
empty (`3b11d83c4892` "AI Discount Vault", re-checked VAD on/off = a **silent visual clip**, marked
honestly), and 1 is a **known dup** (fathom `…pMnAz…` = TrueHorizon Part 1, already on disk 3×; it's
the lone remaining "pending" because its filename doesn't match the harvester's fathom dedup).
- Re-harvested → **104 done / 1 pending** (the dup). Harvested classroom = **drained**.
- The 7 are AIS **community/membership meta-videos** → summarised in
  `knowledge\ais_resources\ais_backlog_drain_2026-06-21.md`. 💰 actionable: post a **"Gem"** = $20 +
  visibility · **539-tool discount vault** (annual perk) · AIS+ pricing **grandfathered** (don't
  cancel casually).
- Logged: `AIS_Audit\audit_log\2026-06-21_audit.md`. Fixed a cp1252 print crash in
  `harvest_ais_loom_urls.py`. Cost €0 (local Whisper, no login).
- **Still deferred** (genuinely NOT captured): NEW classroom modules posted since the last Skool
  snapshot, 16+ YouTube Business Talks behind lazy-load, 1,300+ historical community posts. To pull
  those, re-snapshot the classroom via Playwright (King logs in) → re-harvest → batch-transcribe.

---

## 2026-06-21 (2) · NEW MODULE captured: "Get Your First Clients" (17 lessons)
King: a new module unlocked by Nate → "watch all videos + give me a breakdown." Did the full
**Playwright capture** route (King logged into Skool himself; agent never sees creds):
- Opened AIS+ classroom → King picked module **5 = "Get Your First Clients"** → pulled all **17
  lessons + Loom URLs** from `__NEXT_DATA__` → all 17 NEW (none on disk).
- Transcribed all 17 locally (Whisper, free, batch `firstclients_2026-06-21.tsv`) →
  `transcripts/loom_FIRSTCLIENTS_01..17_*.md`. QA: all real content (~2.3 hrs).
- **Breakdown via Workflow (multi-agent).** First run FAILED silently (args.lessons arrived empty →
  0 grounded agents; lone synthesis agent self-rescued by reading files but per-claim grounding was
  unverifiable). **Lesson: when a Workflow uses scriptPath+args, verify args actually arrived
  (check the `Broke down N/N` log), or hardcode the work-list in the script.** Re-ran with hardcoded
  paths + no schema + timestamp-citation discipline → **17/17 grounded**. Spot-verified numbers vs
  transcripts (Rule of 100, Connects ~$0.15, Upwork 5-10x, $52.50 rate), all matched.
- Output: **`knowledge/ais_resources/first_clients_MASTER_breakdown_2026-06-21.md`** (the deliverable)
  + 3 per-lesson files (`first_clients_lessons_{01-06,07-12,13-17}_2026-06-21.md`). Indexed in
  `ais_classroom_master.md`.
- **The money point for King:** module says his bottleneck (proof + reps, not skill) is exactly
  right; biggest *change* = **run WARM outreach FIRST** (free first project for a case study) before
  cold Upwork, he's spent zero effort there. Plus: fix Upwork profile (lead first 100 chars with one
  real outcome), Rule of 100 (10 primary actions/day part-time), tailored Loom = #1 differentiator.
- Cost €0 (local Whisper). Helpers in `AIS_Audit\.tmp\` (build_drain_batch, first_clients_breakdown.js,
  extract_breakdown).

## 2026-06-21 (2b) · King "do everything, full permission"
- **2nd module captured: "The AI Partner Model"** (6 lessons) → transcribed + grounded breakdown →
  `ai_partner_MASTER_breakdown_2026-06-21.md` (+ per-lesson). Thesis = be the **AI Transformation
  Partner** (find where AI makes a business more money) → value-price → retainer ($3-5k/mo; ~25% of
  project clients upgrade). Nate's US stats, flagged.
- **Delivered to King's phone:** emailed both inboxes + ntfy push = First-Clients breakdown +
  warm-outreach pack (5 humanized DMs) + warm_list.csv + rule_of_100_tracker.csv (`drafts/`).
- **Limits hit/respected:** Sheets API needs re-consent (used CSV instead); did NOT touch the Skool
  payment banner or send DMs/bids (King's rules). Removed 2 fabricated names from the First-Clients doc.
- **Capture method proven repeatable:** King logs into Skool (Playwright) → navigate to course id →
  evaluate `__NEXT_DATA__` for lessons+Loom IDs → dedupe vs disk → batch-transcribe → grounded Workflow
  breakdown. Other modules still available: Build Portfolio + Claude Code (mostly already on disk),
  Live Call Recordings (large), Scale (locked).

## 2026-06-21 (3) · full-classroom sweep ("finish all + only keep relevant, proven reason")
- Swept every accessible module. Status doc = `knowledge\ais_resources\ais_classroom_module_status_2026-06-21.md`.
- **Build Portfolio (49) + Claude Code (48) = already 100% transcribed** (proven via dedupe). Broke down
  the **12 relevant BP lessons** (portfolio/positioning + paid Opportunity-Map discovery) →
  `build_portfolio_relevant_breakdown_2026-06-21.md`. Skipped CC (technical, already distilled) + BP
  Agent-Zero/Phase1/Phase2 + admin modules + locked Scale, each with a stated reason.
- **Live Call Recordings = 118 calls but `video_url` is EMPTY in __NEXT_DATA__** (Skool-hosted player,
  not Loom/YT) → the free yt-dlp+Whisper pipeline CANNOT pull them. To capture a specific call would need
  network-tab stream sniffing per lesson. Crown jewel (TrueHorizon $211k) already on disk. Targeted-only.
- **3 grounded masters now cover the money path:** Get Your First Clients (land it) → AI Partner Model
  (frame it as a retainer) → Build Portfolio (proof + paid discovery/Opportunity Map). 35 lesson
  breakdowns total. €0.
