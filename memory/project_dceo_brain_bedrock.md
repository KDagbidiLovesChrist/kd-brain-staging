# PROJECT · DCEO Brain on Bedrock (work laptop) · the Orcha successor

**Status (2026-07-04 evening): 🟢🎉 THE BRAIN IS ALIVE.** Claude Code v2.1.197 running on **Opus 4.6 (1M context) · Amazon Bedrock** on the work laptop (Git for Windows was the last blocker, fixed via winget). Brain woke in `Documents\DCEO_BRAIN`, introduced itself correctly from its own files, recalled state from the session note. Env vars made permanent via `setx` → VS Code extension wired too. **Day-one additions:** Voice Standard (humanised, per-engineer voice profiles at rollout, NO dashes, no AI slop, reread-before-deliver), operations reality (handovers = Quip doc at night → Slack GC; buildings differ; AWS master protocols outrank local practice; Quip/Slack integration = roadmap item, approval-gated), ROADMAP.md (5 everlasting phases + THE LOOP), TEACHING_PLAN.md (M1-M8 curriculum: two lanes: Lane A GENERAL engineering from model knowledge, Lane B AWS INTERNAL only from King's wiki feeds, never conflated; quiz both directions each module). Trial week = teach M1-M6 + SOP reps + wins.md evidence → manager pitch before burner dies **Jul 11**.

**Update 2026-09-07 (King, verbatim: "i HAVNT SET UP WORK TO AMAZON BEDROCK API I DON'T HAVE YET WITH WORK CREDINITIALS I HAVE PERSONAL ACCOUNT WITH AWS. SO I NEED TO CONNECT THAT TO WORK BRAIN FRON KD ROBOT TO HAVE ROBOT HELP ME WITH WORK"):** the burner died 11 Jul and NO work Bedrock credentials exist today. The work brain has had no model since. King's stated goal: put his PERSONAL AWS account's Bedrock behind the work brain and give it the KD Robot's help. An earlier line in this same session misread "amazon have a bedrock account" as a work account; that was wrong and is withdrawn. Plan under discussion 2026-09-07: personal Bedrock for Lane A / dummy data only until a manager or security yes for site data; the Robot's DNA (skills, SOPs, Logic) goes to work, never its memory; Merlon burner re-check first as the sanctioned free path. King's day-to-day path to his PERSONAL brain from the work laptop is the Claude desktop app signed in as kingdavidagb with an SSH remote into desktop-gruls39 (Claude runs on the Dell, the work laptop is screen and keyboard only). Later the same day, King, verbatim: "HELP ME OPEN MERLO ACCOUNT IF POSSIBLE OR GET AMAZON BEDROCK OR SET UP KIRO AGETS WOTH LOGOS ENGINE IN AMAZON BEDROCK". Door order agreed as the plan: (1) whatever Builder Toolbox already sanctions on the work laptop (Kiro or Claude Code with Amazon-paid model access), (2) a new Merlon burner (Amazon-billed, the July path), (3) personal AWS Bedrock last. Merlon is inside Amazon; Claude cannot reach it, King runs the checklist at the work laptop.

## What this is
The work-only AI brain (DCEO assistant) running on **Claude Code + Amazon Bedrock** on King's WORK laptop. Amazon pays (burner → later a permanent account). Same DNA as the personal brain (read-first, save-always, compounding, /learn·/save·/recover) but **100% work-walled: nothing from it ever enters this repo or any personal system.** This file holds only the setup story + generic knowledge, zero work data, zero keys.

## The vision (King's words, 2026-07-04)
A tool for EVERY DCEO: **master brain** (site knowledge: OPMs, one-lines, procedures, calendars, fed and structured by King) + **personal brain** per engineer (their memory/handoffs). Chief-level standard: it's a TOOL: facts first, sources cited, maths shown, FACT/PATTERN/ESTIMATE labelled, engineer decides, official docs outrank the brain. Dream layer: DCIM-style visual dashboard of building utility/mechanical infra. Ladder: King solo (burner) → permanent account → manager-approved pilot (1-2 DCEOs) → team rollout → dashboard. **Team-scale rollout + sensitive site data = manager approval + security review. Front door only.**

## How we got here (the path that WORKED)
1. Work laptop's only AWS access = `dcgs_internal_ssmRDP` role on a **controls-fleet bastion (prod)** → zero Bedrock perms, wrong place to ask (would be a correct "no").
2. **Isengard/Merlon** (internal AWS account portal) → **Burner Accounts** = self-service sandbox, Amazon-billed, auto-expires. THE sanctioned path for trialling.
3. Created burner **DCEO-claude-bedrock** (expires **Sat Jul 11 2026**). Accepted the AWS Organizations invite (= Amazon pays). Cost Anomaly Detection auto-installed (frugality watchdog).
4. **New Bedrock console = "bedrock-mantle endpoint"** (console region showed Stockholm/eu-north-1): Claude Opus 4.8 / 4.7 / Haiku 4.5 in catalog, priced per M tokens. **API keys page → long-term key** (one key = all models; NOT model-specific; not region-locked).
5. Typing `claude` in cmd on the work laptop → **Amazon's internal Builder Toolbox auto-installed Claude Code** (official internal distribution!) + auto-configured VS Code. builder-mcp registration failed → harmless, continues without.

## Wiring (Windows cmd, session-only, re-set each new terminal)
```
set CLAUDE_CODE_USE_BEDROCK=1
set CLAUDE_CODE_USE_MANTLE=1
set AWS_REGION=eu-west-1        ← try Ireland; fallback eu-north-1 (Stockholm, where catalog was seen)
set AWS_BEARER_TOKEN_BEDROCK=<the burner key, NOT stored in this repo; repo stays zero-secrets>
claude → /status → want "Amazon Bedrock"
```
**Blocker hit & fix:** Claude Code on Windows needs **Git for Windows** (its bash engine) or PowerShell 7. Fix: `winget install --id Git.Git -e --source winget` → fresh cmd → re-set 4 vars → `claude`.

## Gotchas learned (save future sessions)
- **PowerShell vs cmd:** `set X=1` silently does nothing in PowerShell. Type `cmd` first, or use `$env:X="1"`. Long key pastes lose line-breaks/quotes, paste ONE line at a time, verify with `echo %AWS_BEARER_TOKEN_BEDROCK%` (must end `ND0=`).
- **Amazon Q ≠ Bedrock/Claude**: every console error dangles "Diagnose with Amazon Q"; its policies (`AmazonQDeveloperAccess`, all `q:*`) do NOTHING for Bedrock. Ignore the button.
- **Bedrock API key = a copy of your role's badge**: it can't exceed the role's permissions; keys are no bypass for missing IAM perms.
- Website/cloud Claude Code can't do Bedrock; work brain needs the INSTALLED Claude Code (terminal/VS Code ext).
- **Remote Control (`claude rc`) does NOT work on Bedrock** (verified 2026-09-07 from code.claude.com/docs/en/remote-control: needs a claude.ai Pro/Max/Team/Enterprise login, "API keys are not supported", and it is "not available" when you use Amazon Bedrock, Google Cloud, Microsoft Foundry or any custom `ANTHROPIC_BASE_URL`). The only way to see the work laptop in the phone's Claude app would be logging it into King's personal claude.ai, which moves work traffic off Bedrock to api.anthropic.com and breaks the standing walls below. A personal AWS account is no bridge either: it is a customer account outside Amazon's corporate boundary. Do not propose either.
- uBlock blocking `awstrack.me` links in AWS emails = harmless tracking wrappers; never need email links, use Merlon.

## The starter brain (deployed)
15-file pack **DCEO_BRAIN_starter.zip** built + sent in-session (extract → `Documents\DCEO_BRAIN` on work laptop): CLAUDE.md (v2 constitution + chief-level standard) · memory\the_vision + MEMORY index + how_i_work · next-actions · knowledge\dceo_role + site_context · workflow\shift_handover + daily_briefing + ticket_helper · commands\save + recover + learn · sessions\setup note · README_START_HERE. Plus `_imported\` flow: old DCEO_BRAIN design (115 files, personal-laptop-only, deliberately NOT in this repo) → zip → email to work address → brain merges via /learn.

## NEXT (in order)
1. `winget install --id Git.Git -e --source winget` → fresh cmd → 4 set vars → `claude` → `/status` = **Amazon Bedrock** ✅
2. First breath: "Run /recover" → shift_handover SOP on MADE-UP notes → "save this session".
3. Trial week (frugal, dummy data only) → `sessions\wins.md` = the evidence.
4. **Fri Jul 10:** burner dies Jul 11, files/demo survive (laptop-side). Manager pitch WITH proof → permanent account / approved route. Manager one-liner about the burner trial: send if not sent.
5. Phase 2+: permanent home → real shift data (work-side only) → pilot → rollout (approvals first).

## Standing walls (permanent)
- Work brain ↔ personal brain: NEVER mix. DCEO_BRAIN never enters this repo/GitHub/personal cloud.
- Work keys: work laptop only (King chose to keep the burner key in the session chat, accepted for the disposable burner; **rule from Phase 2 on: keys never leave the work laptop**).
- This repo stays zero-secrets: no keys in files, ever.
