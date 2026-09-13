---
name: project_dceo_brain_kiro_migration_2026-08-30
description: "DCEO Brain reconciliation and Kiro migration (Stage 0 complete), work laptop bootstrap (Part B) ready to execute"
metadata: 
  node_type: memory
  type: project
  originSessionId: 99fc6207-9b74-4fbb-9a83-086916c18c2a
  modified: 2026-08-30T20:15:50.700Z
---

# DCEO Brain Kiro Migration (Part A: Planning & Reconciliation)

---

## RULING, 10 September 2026 · THE SHAPE PART B MUST BE EXECUTED IN

King clarified Kiro on 10 Sep: it is an IDE he installs on the work laptop, **Merlon is not needed
to start** (Merlon was in the door order for MODEL access, not to install the IDE), it carries
extensions including GitHub, and **its own bots replace LOGOI on the work side while the brain stays
KD's**.

**The bots ruling is better than routing work through his own engine, and it protects him.** His
Logos engine, his LOGOI agents and his brain then NEVER execute on Amazon hardware. Work uses
Amazon-sanctioned tooling with Amazon-sanctioned models. The intelligence is his; the machine is
theirs. Nothing of his runs on their estate.

### 1 · A SEPARATE REPO. Never `kd-brain`.

```
kd-brain          personal. 1,250 tracked faith files. NEVER on the work laptop.
kd-work-binder    NEW. Skills, SOPs, Logic only. Its own deploy key, scoped to itself.
```

**His personal GitHub token must never sit on the work laptop.** That token reaches `kd-brain`,
`kd-infra` and every private repo he owns, on a machine he does not administer and which his
employer may lawfully inspect. This is the same reasoning that gave Oracle a binder and a per-repo
deploy key rather than the brain and his credential, and the same pattern works here unchanged.

### 2 · THE VALVE RUNS ONE WAY. This is the part that matters most.

King asked for the work brain to carry **network and electrical architecture**. That is Amazon's
confidential data: power topology, one-lines, site network design.

| direction | what | verdict |
|---|---|---|
| **King to work** | his skills, SOPs, Logic, the Robot's DNA | **allowed. It is his IP.** |
| **work to King** | network architecture, electrical, site data, anything Amazon's | **NEVER. It does not leave their estate.** |

Putting Amazon's architecture into a repo on his personal GitHub account is exfiltration regardless
of intent, and intent is not a defence. **This is the same rule as his existing one, facing the other
way:** the Robot's DNA goes to work, never its memory; and their data stays at work, never comes
home.

### 3 · WHAT THIS STILL ALLOWS, which is nearly everything

Kiro on the work laptop, carrying his Logic and his SOPs, reasoning over Amazon's architecture **on
Amazon's machine** with Amazon-sanctioned models. **It is the Klarnow sealed-copy pattern exactly:
his method, their box, their data, their bill.** He invented that shape already; it applies here
without change, and it is the version that survives a security review.

### 4 · STILL HIS HANDS, AND STILL BEHIND THE SOLICITOR

Part B runs on the physical work laptop. And Kiro is the WORK harness, so it sits in the same lane
as the DCEO and PLC vertical: **his Amazon contract needs a solicitor, and that answer should come
before real work data meets any of this.**

---

## Status: Stage 0 (Planning & Reconciliation) COMPLETE

**Date:** 2026-08-30  
**Phase:** Part A (Architecture redesign and document updates on home/reference laptop)  
**Next Phase:** Part B (Work laptop bootstrap and wiki ingestion, when King is on the physical work laptop)

## What Was Done (4 Stages, All Complete)

### Stage 1: Identity + Model Reframing
- Retired "Orcha" as a separate-installed-app framing. Now the working nickname for this Claude-Code-driven persona.
- Note: Real Amazon-internal tool named "Orcha" at `orcha.beta.harmony.a2z.com` exists separately; see `setup\ai_tool_setup.md` for open question on whether it's being replaced by Kiro.
- Model line caveated: direct Opus 4.7 access may route through Kiro (flagged `[VERIFY on work laptop]`)
- Kiro (AWS Bedrock AgentCore, spec-driven agentic IDE) established as primary AI Router target
- Amazon Quick Suite (Q Business successor) established as secondary target
- Sync channel reconciled to Google Drive (was conflicting with OneDrive in some places)
- Version bumped to v2.1

**Files touched:** CLAUDE.md, DCEO_MASTER_CONTEXT.md

### Stage 2: Setup Docs Reconciliation
- Reconciled conflicting bootstrap stories (three different docs had disagreeing paths/names/channels)
- `setup\ai_tool_setup.md`: Reframed as unverified draft adapted from legacy Orcha install; flagged all Kiro-specific details for on-laptop verification
- `setup\work_laptop_setup.md`: Archived (described dead pre-v2 structure); replaced with pointer to canonical WORK_LAPTOP_BOOTSTRAP.md
- `WORK_LAPTOP_BOOTSTRAP.md`: Now the single canonical guide; added Kiro awareness note, model caveat, Phase B wiki-ingestion priorities

**Files touched:** setup/ai_tool_setup.md, setup/work_laptop_setup.md, WORK_LAPTOP_BOOTSTRAP.md

### Stage 3: AI Router Population
- Replaced generic placeholder skeleton with three concrete known candidates
- Decision tree: Kiro (agentic/spec-driven) → Quick Suite (enterprise search/assistant) → Claude Code inline (fallback)
- Added Kiro setup recipe to install playbook (status: PROPOSED, needs on-laptop verification)
- Updated Population Status checklists to include verification boxes for Kiro/Toolbox and Quick Suite team access

**Files touched:** knowledge/ai_tool_router.md, commands/ai_router.md, knowledge/install_playbook.md

### Stage 4: Privacy Boundary Fix (Critical)
- Completely rewrote `commands\lifecycle\save.md` to be DCEO-work-scoped only
  - Removed all personal project rows (AIS Challenge, Newsletter, Lead gen, Fiverr gig, Money Progress, etc.)
  - Replaced personal home-brain paths with DCEO-only paths
  - Routing table now references only DCEO work files
- Completely rewrote `commands\lifecycle\context.md` to be DCEO-work-scoped only
  - Removed reference to personal home-brain directory
  - Scan scope now references only local work-laptop path
- **Impact:** King can now safely run `/save` on work laptop without leaking personal home-brain content into DCEO-shared files

**Files touched:** commands/lifecycle/save.md, commands/lifecycle/context.md

## Known Gaps (Low Priority, Deferred)

- `memory\reference_*.md` files may have some personal-brain echoes (low-priority cleanup)
- Some `commands\orcha\` skill files still reference `DCEO_SKILLS\knowledge\` (old v2 path) instead of `knowledge\` (current path): mechanical cleanup, non-blocking

## Three Open Unknowns (Resolve in Part B, Step 8)

These must be confirmed live on the work laptop during Phase B wiki ingestion:

1. **Is the internal Orcha app (`orcha.beta.harmony.a2z.com`) actually Kiro's predecessor at Amazon** or are they unrelated tools that happen to share a name?
2. **Is Kiro installable via the work laptop's Toolbox, and does Midway auth apply the same way** (like the legacy Orcha app)?
3. **Confirmed facts** must be written back into `knowledge\amazon_ai_wiki.md` and `setup\ai_tool_setup.md`'s `[VERIFY:]` placeholders before proceeding.

## Next Step: Part B (Work Laptop Bootstrap)

Execute `WORK_LAPTOP_BOOTSTRAP.md` Steps 1 through 8 end to end when King is physically on the work laptop.

**Critical focus in Step 8 (Phase B: Wiki Ingestion):**
- Prioritize Kiro + Quick Suite entries in the Amazon AI wiki
- Resolve the three unknowns live
- Update `knowledge\amazon_ai_wiki.md` with confirmed facts
- Update `setup\ai_tool_setup.md`'s `[VERIFY:]` placeholders with real answers

Once Part B is done, the AI Router becomes operational with real internal tools, and the brain is ready for live DCEO shift work.

## Reference

- Plan file: `C:\Users\Dell\.claude\plans\hi-what-env-are-cuddly-pumpkin.md`
- Handoff: `C:\Users\Dell\.claude\handoffs\handoff_2026-08-30_00-00_save.md`
- Related: [[feedback_dceo_brain_privacy_boundaries]]
