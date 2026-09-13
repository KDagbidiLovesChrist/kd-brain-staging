---
name: dashboard-os-build-reference
description: "Consolidated build reference for AI-agent dashboards / business OS systems - visual design patterns, concrete build stacks, GitHub evaluation, and the creator/reference map. Built for the Klarnow prototype but written to be reused for any future dashboard/brain build."
metadata:
  type: reference
---

# Dashboard / AI-Agent-OS Build Reference (compiled 2026-08-06)

Built for [[project-klarnow-os-deal]] but intentionally general - reuse this for any future client
dashboard or "brain" build. Compiled from 4 videos watched in full (not summaries) + 7 scout-agent
research passes across GitHub, YouTube, and the open web. Full source videos: `knowledge\video_studies\`.

## The visual design pattern (what a good agent dashboard LOOKS like)
From Bennett Spooner's "Optimal Engine" (full write-up: `knowledge\video_studies\2026-08-06_bennett_spooner_optimal_engine_dashboard_ref.md`):
- **Two linked views of the same agent data:** a circular force-directed network graph (department
  nodes radiating from a center) AND a hierarchical org chart (Company -> Coordinator -> Departments ->
  named agents). Same underlying data, two lenses.
- **Per-agent config panel on click:** PROMPT ASSUMPTION (plain-English job description) / FILES /
  RUN_COMMANDS / MESSAGES / NOTES. Node actions: Add Node, Remove Node, Set Parent, Set Child, Send Chat,
  Send File.
- Separate tabs for PERFORMANCE / REVENUE / MODEL / FUNNEL metrics.
- **Caveat:** this is a control-panel demo, not proof the agents run live end to end. Copy the visual
  language, not the "37 agents" headcount.

## Two proven build stacks (pick by speed vs. robustness)

### A. Fast/simple - single HTML + Claude + Vercel + Supabase (~1 day, near-zero cost)
Watched in full: "I Built My Own Dashboard With Claude (Personal Jarvis)" -
https://www.youtube.com/watch?v=bap3i8R8sOw
1. Prompt Claude for an interactive dashboard HTML file, iterate with design references (screenshot of
   a target look works directly as a prompt input).
2. VS Code + "Claude Code" extension, logged in.
3. Node.js + Vercel CLI (`npm install -g vercel`, `vercel login`).
4. Supabase project for persistence: one table (`dashboard_state`, jsonb column, RLS policy "allow all"),
   SQL pasted into Supabase's SQL Editor.
5. `vercel login` then tell Claude Code "read index.html and deploy to vercel" - it handles the deploy.
6. Send the Vercel URL to a phone, "Add to Home Screen" for an app-like client experience.
- **Real cost quoted:** ~$30 one-time-feeling (Claude usage) instead of stacking multiple $/mo tracking
  apps. No Vercel/Supabase cost at this scale.
- **Best for:** the V1 "simple dashboard" deliverable in the Klarnow brief - fastest path to something
  real and demoable.

### B. Robust/scalable - React Flow + Next.js + SQLite/Postgres + Vercel (~1-2 weeks)
From the GitHub-criteria research pass (criteria used: maintenance activity, adoption/stars, docs
quality, license, architecture fit, deploy ease, community health - applied to real repo stats, not
just reputation):
- **Do NOT fork** the low-adoption "agent dashboard" repos found (agent-swarm-dashboard: 5 stars;
  openclaw-mission-control: 0 stars/adoption) - too immature, higher risk than building fresh.
- **Use React Flow directly** (37k stars, MIT, 213k weekly downloads, industry-standard node-graph UI)
  over Cytoscape.js (built for dense data-analytics graphs, overkill/wrong fit here) as the graph engine.
  Pair with Dagre for the org-chart/hierarchical layout.
- Full frameworks (LangGraph Studio, AutoGen Studio, Langflow) are agent **orchestration**, not dashboard
  UI - they don't solve the visual layer, only the backend agent logic. Don't expect them to hand you the
  Bennett-Spooner-style dashboard for free.
- One repo worth a look as architecture reference (not a fork target): AndrewKochulab/jarvis-dashboard
  (Obsidian-based, modular, agent-fleet monitoring pattern) - `github.com/AndrewKochulab/jarvis-dashboard`.
- **Best for:** once a client relationship is proven and it's worth investing in something that scales to
  "many brains" (King's actual end-goal for Klarnow, per [[project-klarnow-os-deal]]).

## The 5-layer "AI OS" architecture (not just UI - what makes it actually work)
From "I Built My Own JARVIS with Claude Code (100% FREE)" -
https://www.youtube.com/watch?v=FzE-UYBe8co - watched in full. This is the most technically substantive
of the four videos and maps closely onto King's own existing CLAUDE.md/memory architecture already:
1. **Identity** - who it works for, how it speaks, what it optimizes for (= King's own CLAUDE.md "Who I
   Am" section).
2. **Tools** - what each tool does and the exact moment to reach for it (= MCP servers).
3. **Memory** - clients, pricing, preferences, past decisions, persisted across sessions (= King's own
   `memory/` folder pattern).
4. **Triggers** - phrases that fire a whole multi-step workflow (= King's own `/commands`).
5. **Guardrails** - nothing leaves the machine without approval; read-only by default, edits only on
   explicit instruction; one auditable place to find/fix issues. Direct quote worth keeping: *"If you
   skip the guardrail step, you honestly don't have an AI assistant, and you probably have a liability."*

**Real cost breakdown quoted:** Claude Pro ~$20/mo + ElevenLabs free tier (voice out) + free speech-to-
text + $0 hosting (own machine) = ~$20/mo total, vs. a naive build at ~$273/mo (Claude Max + paid LLM API
+ paid voice + a server). Optional: ~$6/mo VPS (e.g. Hostinger) if it needs to run 24/7 instead of only
when a laptop is on.

**Honest caveat from the video itself:** "$0 cost" and "30 minutes" and "runs my entire business" are all
oversold in the marketing framing - real cost is ~$20/mo (assumes an existing Claude Pro sub), and the
"prompt" you paste is itself a large structured spec, i.e. still real configuration work, not truly
code-free.

## MCP integration pattern (how the dashboard talks to real business tools)
From Chanyoung Ryu (Chandler)'s reel, reacting to the original @lukebuildsai JARVIS format - full
write-up in `knowledge\video_studies\` (see below). Shows a working pattern: Claude Code + `/voice` +
ElevenLabs voice output, wired to RevenueCat MCP (app revenue), Buffer MCP (social posting), Meta Ads MCP
(ad spend/ROI - flagged with healthy skepticism about Meta's own incentives there), Gmail MCP (customer
email, autonomously resolved 13/18 emails in one week per the demo), plus **named custom subagents**
("Tom, the developer agent", "Scout") that the main agent hands off work to. This is the direct pattern
for Klarnow's own named agents (Lead/Follow-up/Booking/Onboarding/Founder-clone/Campaign-builder/
Operator per the brief).

## The creator/reference map
- **Bennett Spooner** (@bennettx.ai, IG 19K followers) - founder of **OperatorOS**, AI agent automation
  for service-based franchises (CRM integration, sales/recruiting/finance/marketing). The "Optimal
  Engine" dashboard is his own product demo. Real operator, not just a hype account.
- **Luke Cutting** (@lukebuildsai, co-founder Azaris AI) - the ORIGINAL "build your own JARVIS" creator
  that Chanyoung Ryu's video was reacting to. Has a paid course (lukebuildsai.com, "JARVIS Agent Crash
  Course"). Claims tripled his own app's MRR in one month using this pattern. YouTube:
  youtube.com/channel/UCSssB2TncrhoTVIi-gQk9Kg, TikTok: @luke.builds.ai.
- **Chanyoung Ryu ("Chandler")** - newer creator, Instagram-based, explicitly building on/crediting
  Luke's original idea with his own from-scratch walkthrough. Channel is brand new as of this reel.
- **Nate Herk** - King's existing WAT-framework instructor (AI Automation Society, 850k+ subs). Confirmed:
  his lane is **n8n no-code workflow automation**, not visual AI-agent dashboards - don't expect
  dashboard-specific content from him; he's the right reference for the automation/workflow layer, not
  the UI layer.

## What to do with this (for the Klarnow build specifically)
- **V1 (14-day prototype, per the brief):** use build-stack A (single HTML + Claude + Vercel + Supabase)
  for speed, styled toward Bennett Spooner's network-graph + org-chart visual language, structured
  internally on the 5-layer architecture (Identity/Tools/Memory/Triggers/Guardrails) since that's already
  proven and maps onto King's own working system.
- **Longer-term "many brains" vision:** migrate to build-stack B (React Flow + Next.js) once the
  relationship justifies the investment - don't over-build V1.
- **Don't** fork the low-star GitHub "agent dashboard" repos found during research - they cost more in
  rework than building fresh.

## Sources (full watch/research trail)
- `knowledge\video_studies\2026-08-06_bennett_spooner_optimal_engine_dashboard_ref.md` - full frame-by-
  frame Bennett Spooner watch.
- Videos watched in full via Gemini (not summary-only): bap3i8R8sOw (Command Center tutorial),
  FzE-UYBe8co (JARVIS 5-layer architecture), the Chanyoung Ryu Instagram reel
  (instagram.com/reel/DZVXehQRe3T/).
- GitHub criteria research pass: real stats checked directly (stars/forks/last-commit/license) for
  Smilkoski/agent-swarm-dashboard, Mikael-Lelouch/openclaw-mission-control,
  hoangsonww/Claude-Code-Agent-Monitor, Azim-Ahmed/Automation-workflow, reactflow.dev, js.cytoscape.org.
- Creator research pass: Bennett Spooner (OperatorOS/bennettx.ai), Luke Cutting (lukebuildsai.com), Nate
  Herk (nateherk.com) confirmed via WebSearch cross-check, not single-source.
