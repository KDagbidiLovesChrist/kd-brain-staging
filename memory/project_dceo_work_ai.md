---
name: project-dceo-work-ai
description: "DCEO Brain (Orcha), Phase A REBUILD COMPLETE 2026-05-23 evening. DCEO_BRAIN\\ folder is identity-neutral, on Google Drive, ready for work-laptop pickup. Phase B = wiki ingest on work laptop."
metadata: 
  node_type: memory
  type: project
  originSessionId: 07c00cf0-b55d-4de7-a668-79dbbed25d9d
---

# DCEO Brain (Orcha) · Status as of 2026-05-23 evening

## TL;DR
**Phase A complete.** `DCEO_SKILLS\` renamed to **`DCEO_BRAIN\`**, fully rebuilt as identity-neutral team-shareable brain, scrubbed of all King David references, synced to Google Drive (113 files), ready for work-laptop bootstrap.

**Phase B = tomorrow on work laptop.** Ingest Amazon's internal AI wiki → populate `knowledge\amazon_ai_wiki.md` + `knowledge\ai_tool_router.md` + `commands\ai_router.md` → run first real morning briefing. *(⚠️ LAPTOP-ONLY: these are DCEO_BRAIN work-laptop paths, not this repo.)*

**Slack Phase 2 = POSTPONED, NOT KILLED.** All 8 Slack bot files preserved in `_archive_pre_v2_2026-05-23\slack_bot\`. Manager demo focus shifted to Claude Code workflow (not Slack).

---

## What "Phase A" actually means (built 2026-05-23 evening)

| Layer | Built |
|---|---|
| Root | `CLAUDE.md` (identity-neutral, 224 lines) · `DCEO_MASTER_CONTEXT.md` v2 (Orcha persona + AI router rules + multi-agent dispatch, 200 lines) · `dceo_demo_v2.html` (488-line manager WOW demo) · `.env.template` · `WORK_LAPTOP_BOOTSTRAP.md` |
| `memory\` | 35 files = 16 TRANSFER_AS_IS universal refs + 10 scrubbed feedback + 8 already-generic feedback + `MEMORY.md` index |
| `knowledge\` | 13 files = 5 existing role files (dceo_knowledge, email/incident/ticket patterns, escalation procedures) + 5 transferred/scrubbed (ecosystem_architecture, workflow_patterns, patterns, tools_learned, system_explained) + 3 NEW (amazon_ai_wiki placeholder, ai_tool_router placeholder, install_playbook) |
| `commands\` | 23 skills total: `orcha\` (6 admin skills) + `lifecycle\` (4: save/recover/handoff/context) + `intelligence\` (2: search/research) + `multi_agent\` (4: agent_team/orchestrate/subagent_registry/master_prompt) + 5 specialist (browser/deploy/excalidraw_visuals/proposal/cold_email) + work_exec (re-scoped /exec) + ai_router placeholder |
| `_archive_pre_v2_2026-05-23\` | 23 files preserved: old DCEO_BRAIN_WORKFLOW, DCEO_FRAMEWORK, dceo_organiser, DCEO_COLLEAGUE_GUIDE, slack_bot\ (8 files), old admin/email/operations/risk subfolders |

## Privacy wall verification
**PASSED.** Final grep across every `.md` / `.html` / `.py` outside `_archive` for "King David | Joshua | Fiverr | plumber | Eastern Orthodox | kingagbidi | Kingdavidagb" returned ZERO hits. Identity-neutral throughout.

## Identity-layer scope (CRITICAL · recorded so future sessions don't get confused)
| Layer | Knows King David? | Purpose |
|---|---|---|
| Work laptop's outer `.claude\CLAUDE.md` | YES · his personal Claude install on the work laptop, used to help him set up + operate DCEO Brain | Personal collaborator layer |
| `DCEO_BRAIN\` folder + Orcha persona inside | NO · fully sterile, other DCEOs use the same folder | Shared team brain |

Other DCEOs activating Orcha see the same neutral persona. Per-DCEO context lives in `personal\dceo_personal_<name>.md` (LOCAL ONLY, never uploaded, never written to disk by Orcha).

## Google Drive sync
- **113 files uploaded** preserving folder structure
- **URL:** https://drive.google.com/drive/folders/1uI_176ng0nWPBhTLe4WQsKuFihramytO
- **Sync script (reusable):** `C:\Users\Dell\.claude\tools\sync_dceo_brain_to_drive.py`, uses existing `token.json` from `tools\google_auth.py`
- Re-run on future updates to push deltas

## Phase B · Work Laptop Tasks (next session)
Follow `DCEO_BRAIN\WORK_LAPTOP_BOOTSTRAP.md` step-by-step:
1. Download `DCEO_BRAIN\` from Google Drive → `C:\Users\<workuser>\.claude\DCEO_BRAIN\`
2. Install Claude Code if needed
3. Copy `.env.template` → `.env`, populate Bedrock block (region + role ARN)
4. Install AWS CLI + configure profile, verify Bedrock Opus 4.7 access
5. Create `personal\dceo_personal_<name>.md` (local-only, never synced)
6. Run verification gate test, Orcha should greet, confirm 7 skills + lifecycle + multi-agent loaded, NDA active, HITL active, Bedrock 4.7
7. Test morning briefing
8. **The Wiki Ingest**, Playwright through Amazon's internal AI wiki, distill into `knowledge\amazon_ai_wiki.md`, build `ai_tool_router.md` decision tree, populate `commands\ai_router.md` *(LAPTOP-ONLY: DCEO_BRAIN work laptop)*
9. Real-task test: "I need to do X, which AI?" → should route correctly

## Pricing / cost · King David pays £0
| Service | Pays |
|---|---|
| Bedrock Opus 4.7 | Amazon |
| Future Lambda + Bedrock Agents (if Phase 2 unfreezes) | Amazon |
| Storage / Knowledge Base | Amazon |
| King David personal | £0 |

## Slack Phase 2 (POSTPONED)
- Code preserved in `_archive_pre_v2_2026-05-23\slack_bot\` (8 files: lambda_function.py, dynamodb_setup.py, s3_setup.py, approval_dashboard.html, deploy.md, Dockerfile, requirements.txt, .env.template)
- Re-activate when team decides Slack is the right delivery surface
- Install recipe: `knowledge\install_playbook.md` § Slack Bot (Phase 2, currently postponed) *(LAPTOP-ONLY: DCEO_BRAIN work laptop)*

## Manager demo
- `dceo_demo_v2.html`, single-file HTML, brand-compliant (Navy #0A1628 · Gold #C9A84C · Off-White #F8F6F1)
- 4 sections: What Orcha Does · 6 Skills · How A DCEO Uses It (Claude Code workflow, NOT Slack) · Time Saved Per Shift (1-2 hrs/shift, breakdown)
- Open by double-clicking, no build step

## Critical Constraints (unchanged)
- NEVER touch live Amazon alarms or monitoring
- NEVER write confidential data to disk
- NEVER use a personal API key, Bedrock-only
- HITL non-negotiable, Orcha drafts, the DCEO sends
- NDA filter on every handover doc, describe what was DONE, never what was SEEN
