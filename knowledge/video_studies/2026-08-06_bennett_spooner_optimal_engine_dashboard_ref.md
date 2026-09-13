---
name: video-study-bennett-spooner-optimal-engine
description: "Reference reel Goodness (Klarnow) shared showing the dashboard/ecosystem style he wants - Bennett Spooner's 'Optimal Engine' 37-AI-agent control panel. Watched directly (recorded + Gemini analysis), not summary-only."
metadata:
  type: reference
---

# Bennett Spooner | AI Automation - "Optimal Engine" (watched 2026-08-06)

**Source:** https://www.instagram.com/reel/DbcPo0dMQ3d/ - shared by Goodness in WhatsApp 2026-08-05 05:38,
caption text: *"Took 2 months to build this... but the most important thing I learned was functionality
over everything. Comment 'founder' and I'll send over the OS demo. I probably put 100+ hours into this
my github commit history is crazy."*

**Why this matters:** on 2026-08-05 in WhatsApp, right before this link, Goodness wrote *"I acc never got
to show you my brain centre and dashboard and eco system"* - this reel is his reference point for how he
wants Klarnow's own dashboard/ecosystem to look and feel. Treat this as the VISUAL/UX brief, not a literal
build spec (see caveats below). Related: [[project-klarnow-os-deal]].

## How it was watched
Recorded live (Playwright, 90s screen-capture of the actual reel playing at full resolution in a logged-in
browser session, not a downloaded/cropped clip) + analysed frame-by-frame via Gemini + cross-checked with
a WebSearch on the creator. Full watch, not summary-only.

## What the dashboard actually shows (the objective lesson)
A UI called **"Optimal Engine"** that visualises and manages a **37-agent AI company** two ways:
1. **A circular network graph** (force-directed, one central node, department nodes radiating out,
   labelled AUDIT / SALES / COMMUNICATIONS / MARKETING-GROWTH / TECH / CLIENTS) - the "living brain" view.
2. **A hierarchical org chart** ("AGENT HIERARCHY"): BENNETT GROUP -> COORDINATOR -> OPERATIONS / SALES /
   MARKETING-GROWTH / TECH -> named sub-agents (e.g. under TECH: Dev Agent 1, Dev Agent 2, QA Agent 1,
   Security Agent 1) - the "org chart" view of the same data.

Clicking into any node opens a **per-agent configuration panel** on the left with a consistent schema:
- PROMPT ASSUMPTION (what the agent believes its job is, in plain English)
- FILES / RUN_COMMANDS (e.g. a literal `git add . / git commit -m "..." / git push` shown for one agent)
- MESSAGES (the channel/inbox that agent reads)
- NOTES (edge-case clarifications written in plain English, e.g. defining what "broken link" means for
  that agent)
- Node actions: Add Node / Remove Node / Set Parent / Set Child / Send Chat / Send File

Example agent shown in full: **DIGEST_AI_AUDITOR** - reads every channel, flags messages to remove, sends
a 24h digest, audits "brain-store mechanism health" (their term for their own knowledge base). A second
agent, **AUDIT - Brain-store mechanism health**, breaks into named sub-functions: RUN_FILE_ADDER (find
broken links/stale data, try to fix), LOG_CLEANER (remove worst offenders), CHATBOT, PROMPT WRITER,
SUMMARY BUILDER - essentially a self-maintaining knowledge base janitor.

Separate dashboard tabs for **PERFORMANCE, REVENUE, MODEL, FUNNEL** - shown as tables/graphs but the video
never lingers long enough to read real numbers off them (see caveats).

## What's substantiated vs hype (be honest, per the /watch rule)
- **Substantiated:** the UI genuinely renders a live, clickable agent network with real per-agent config
  (prompts, run-commands, files) - this is a real control-panel, not just mockup screenshots.
- **NOT shown:** the agents actually executing/running live, or any real output. It's a control panel demo,
  not proof the 37 agents work end to end. "2 months, 100+ hours, crazy commit history" is the creator's own
  unverified claim. Treat the visual/UX language as the reusable part, not the underlying engineering as a
  benchmark to match.
- **Second source (2026-08-06):** Bennett Spooner is a real AI-automation builder, founder of **OperatorOS**
  (AI agents automating service-based franchises, plugging into CRMs like ServiceTitan across sales,
  recruiting, finance, marketing, comms) and Merydian; active creator across IG/TikTok/YouTube/X, sells via
  Whop. This is a real, working AI-automation operator, not a random hype account - the reference is a
  reasonable one for Goodness to be pointing at.

## What this means for the Klarnow build specifically
Goodness wants Klarnow's "brain centre" to visually read as **one living network of specialised agents per
client business**, grouped by department, each inspectable down to its own prompt/config - not a flat
dashboard of numbers. This maps directly onto what the brief already describes (8 named agents across
Lead/Follow-up/Booking, Onboarding/Founder-clone/Campaign-builder, Operator) and onto **King's own existing
brain-data-centre visualisation work** ([[reference-brain-dcim]], `tools\build_brain_dcim.py`,
`_datacentre\halls\`) - structurally the same idea, already partly built for King's own brain. That existing
pattern (not a from-scratch build) is the strongest starting point for Klarnow's V1 "simple dashboard"
deliverable and the longer-run "many brains" vision.

## What to do
- When designing Klarnow V1's dashboard screen, reference this reel's two views (network graph + org chart)
  and the per-agent config-panel schema (prompt / files / run-commands / messages / notes) as the visual
  target Goodness has in mind - reuse King's own DCIM/EDEN visual language as the technical starting point,
  don't build the look from zero.
- Don't chase "37 agents" or the specific department names literally - Klarnow's own agent set (per the
  brief) is smaller and already named; match the STYLE, not the headcount.
- Nothing to action on the "2 months / 100+ hours" claim - it's just creator framing, not a spec.
