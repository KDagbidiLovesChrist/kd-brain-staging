# THE KING DAVID AI ARCHITECTURE · ONBOARDING v9
*Rewritten 2026-07-04 (post-reorg) · v8 preserved in git history · under 400 lines · same plain English, no jargon.*

> The canonical mental model of the whole system. Read this once and you understand how the brain works. For the law itself, read `CLAUDE.md` (the constitution). For the memory index, read `memory\MEMORY.md`. For tactical AIS findings, read `knowledge\ais_master_summary.md`.

**What changed in v9 (the 2026-07-04 reorg):** CLAUDE.md slimmed 395 to 94 lines with the dashboards split into satellite files. 25 Operating Rules now (was 18). MONEY MODE is on: the brain is finished, every session defaults to the first euro. `/qa-master` added as the adversarial inspector. `rules\` path-scoped rules, `decisions\log.md`, `AGENTS.md` and the cadence layer are new. `/studynotes` is retired. AIS LIVE is skipped live; we chase the recordings.

---

# PART 1 · FOUNDATIONS

## 1.1 · Vocabulary

| Word | What it is | Restaurant analogy |
|---|---|---|
| AI | Umbrella term | Cooking (the field) |
| LLM | The brain (Claude) | The chef's brain |
| Agent | LLM + loop + tools + goal | Chef with hands + recipe + kitchen |
| Tool | A function the agent calls | Knife / pan / oven |
| API | Address + key to call somebody's service | Phone line to a supplier |
| MCP | Universal plug for new tools | Standardised socket |
| Skill | A `/command` that loads workflow + tools | "Order the chef's special" |
| Harness | The wrapper running the LLM (= Claude Code) | The whole kitchen |
| CLAUDE.md | Always-loaded instruction file | Note pinned to chef's apron |
| Hook | Script that fires on an event | Motion-sensor light |
| Webhook | URL another service hits when X happens | The doorbell (UPS rings) |
| Routine | A cloud schedule that runs with the laptop off | A supplier who delivers while you sleep |

## 1.2 · WAT + L (Nate Herk's framework · King David adopted it)
*Attribution: Nate teaches WAT in AIS+ Claude Code Phase 2 Module 1.3. Credit Nate when pitching. "Logic" is King's own faith-naming of the skill layer.*

```
W = Workflow   →  markdown SOP (the steps)
A = Agent      →  Claude reads, reasons, decides
T = Tool       →  Python / MCP / API does the work
L = Logic      →  the /command that runs the chain (the Word)
                    ↓
                  MONEY (the fruit, for God)
```
Logic = from **Logos**, the Word, Christ (John 1:1). Every command is rooted in Him. See `_ops\CREED.md`. Every piece is swappable: stable interface, swappable internals.

## 1.3 · Three Ms · client-facing version
- **Memory** = knowledge base + rules (CLAUDE.md + memory)
- **Mechanics** = workflows + automations (skills + tools)
- **Monetisation** = how the client makes money (mapped to their pain)

Use WAT internally. Use Three Ms when pitching.

## 1.4 · Why CLAUDE.md exists (and why it is now small)
Every session, the harness auto-loads the master `CLAUDE.md` plus a project `CLAUDE.md` if one exists. Without it, every session starts with a stranger. With it, every session starts with your business partner.

The 2026-07-04 reorg proved something important: a HUGE instruction file gets obeyed WORSE. Anthropic docs plus four independent operator guides all agree the sweet spot is 80 to 200 lines. So the master CLAUDE.md is now **94 lines**: identity, the goal, WAT, the 25 rules, brand, one-line project dashboard, pointers. The dashboards moved into satellites (Part 3). The rules are the law; the dashboards are just data.

## 1.5 · Nate Herk's AIS courses
AI fundamentals, prompting, agents, n8n, tools/APIs/MCPs, deployment, monetisation. **Thesis: AI is plumbing, not magic.** Inputs, logic, outputs, money. The Skool community layers on live calls, daily wins, workflow templates and peer accountability. **The community is the moat.** AIS LIVE (Jul 11-12) is skipped live; the recordings get chased after the guarded weekend, plus a Day-2 close-the-client summary.

---

# PART 2 · THE HARNESS

## 2.1 · What Claude Code is
The wrapper. Claude is the LLM; Claude Code is the program running Claude on your machine (and now also in the cloud). It manages conversations, gives Claude tools, auto-loads CLAUDE.md + memory + skills, enforces permissions, fires hooks.

**Doors into the same brain:** the laptop (VS Code extension or CLI) · the phone (Claude app, Code, "KD Laptop Brain" remote control) · Claude Code on the web (cloud sessions + Routines that run with the laptop OFF).

## 2.2 · Modes

| Mode | What | When |
|---|---|---|
| Default | Anything within permissions | Normal work |
| Plan mode | Read-only + plan file | Design before building |
| Ask mode | Read-only, no writes | Pure questions |
| Bypass mode | All prompts skipped | Trust me fully this session |

## 2.3 · Tool universe

| Category | Tools |
|---|---|
| File ops | Read · Write · Edit · Glob |
| Search | Grep (ripgrep) |
| Shell | Bash · PowerShell |
| Web | WebFetch · WebSearch |
| Browser | Playwright MCP |
| Scrape | Firecrawl MCP · Apify |
| Subagents | Agent (Explore · general-purpose · Plan) |
| Google | Gmail + Sheets + Drive + Calendar via `tools\google_auth.py` |

Some tools are deferred; `ToolSearch` fetches their schemas on demand. That saves context. The full live registry with statuses is `knowledge\TOOLS_CONNECTED.md` (not duplicated here on purpose, one source of truth).

---

# PART 3 · THE ARCHITECTURE AFTER THE REORG

Think of it as a small constitution with a library around it.

```
CLAUDE.md (94 lines)        THE CONSTITUTION
  identity · goal · WAT · 25 rules · brand · 1-line dashboard · pointers
        │
        ├── knowledge\SKILLS_INDEX.md      all skill tables (the 111)
        ├── memory\ACTIVE_PROJECTS.md      full project histories + badges
        ├── knowledge\TOOLS_CONNECTED.md   every tool/API/MCP + status
        ├── knowledge\DEV_ZONES.md         build zones · SKIP table · AIS history
        ├── knowledge\BRAIN_WIRING.md      RAG · memory system · file pipeline · setup guides
        │
        ├── rules\                          path-scoped rules (load per folder)
        │     faith.md (the-truth) · video.md (content) · money.md (earning)
        ├── decisions\log.md                append-only ledger of King's calls
        ├── AGENTS.md                       bootstrap for ANY harness (Codex, Cursor, Llama...)
        └── _ops\                           the law: FOUNDATION_PIPELINE · TRUST_LEDGER ·
                                            CREED · OPERATING_RHYTHM · SKILL_TIER_LEDGER
```

**Why satellites?** The rules stay in front of Claude every second; the data loads only when needed. Sharper obedience, fewer tokens.

**`rules\`** = path-scoped law. Working in `the-truth\`? `rules\faith.md` loads. Working in a content folder? `rules\video.md`. Earning folders? `rules\money.md`. On the laptop this repo IS `.claude`, so `rules\` = `.claude\rules\`.

**`decisions\log.md`** = one line per King decision, newest first, never edited. The quick ledger every session can trust ("MONEY MODE 07-02", "WhatsApp cold sends KILLED 07-03", "/qa-master adopted 07-04").

**`AGENTS.md`** = the multi-harness bootstrap. Any AI harness landing in the repo (not just Claude Code) reads it and gets pointed to CLAUDE.md, the pipeline, the memory index and the no-secrets rule.

## 3.1 · Standard WAT project template (unchanged, now automatic)
Every new project gets this via `/new-project` (Rule #14, scaffolded from `templates\project-template\`):
```
<Project>\
├── CLAUDE.md       ← first line: "READ FIRST: master CLAUDE.md"
├── MANIFEST.md     ← live list of tools/skills/APIs/key-files used
├── .env            ← API keys (never commit)
├── sessions\       ← every project session logged
├── workflow\       ← W: SOP markdown
├── tools\          ← T: Python scripts
└── commands\       ← L: project-local skill (optional)
```

## 3.2 · Project lifecycle
```
IDEA → BUILD → Tested (/qa + /qa-master) → KING approves → Trusted → PRODUCTION
```
That gate is the Foundation Pipeline (`_ops\FOUNDATION_PIPELINE.md`), the one law every task follows, at every scale. It runs both ways: build up 0 to 100, recover down 100 to 0 from any phase. Every shipped piece becomes a trusted stone in `_ops\TRUST_LEDGER.md`.

---

# PART 4 · MEMORY, KNOWLEDGE AND THE SAVE PIPELINE

## 4.1 · Memory vs Knowledge (one line each)
- **Memory** (`memory\`) = facts about *King and how to work with him*. Four types: `user_*` · `feedback_*` · `project_*` · `reference_*`. Index = `MEMORY.md`, read at session start.
- **Knowledge** (`knowledge\`) = facts about *the work itself*. The RAG base, queried by `/search`. `/search` reads ALL of `memory\` + `knowledge\` + `inbox\`.

**Two-step save:** write the memory file with frontmatter, then add a one-line pointer in `MEMORY.md`. Detail lives in the file; the index stays tight.

**The vault:** the `.claude` brain IS the Obsidian vault now (one source of truth, no copy). The old separate `Documents\Brain` vault was archived, which is why `/studynotes` is retired (Part 5.3). Quick captures go in `inbox\`; `/learn` files them properly.

## 4.2 · The full save pipeline (post-reorg truth)

```
DURING SESSION
You teach me / correct me            You ship a pattern
  → write memory file                   → append to knowledge\
  → pointer in MEMORY.md                → queryable by /search

Project status changes
  → update memory\project_*.md
  → badge + history in memory\ACTIVE_PROJECTS.md   ← the badges live HERE now
  → refresh the ONE-LINE dashboard entry in CLAUDE.md (nothing more)

King makes a call
  → one line appended to decisions\log.md

AUTOMATIC (hooks · you do nothing)
SessionStart → tools\session_start_brief.py   (cross-session brief, Rule #15)
PreCompact   → tools\precompact_save.py       (auto-save before context squeeze)
Stop         → auto-handoff → handoffs\

END OF SESSION
/save → handoff file + memory routing + ACTIVE_PROJECTS badges (Rule #10: never skip)

NEXT SESSION
Harness loads CLAUDE.md + rules → SessionStart brief fires → /recover if needed
```

The key change from v8: project badges and histories update in `memory\ACTIVE_PROJECTS.md`, NOT inside CLAUDE.md. CLAUDE.md keeps only the one-line-per-project dashboard.

---

# PART 5 · SKILLS · "LOGIC"

## 5.1 · The count and where to look
**111 skills: 54 `/command` skills in `commands\` + 57 installed plugin skills in `skills\`.** Type `/` in Claude Code to see them all. Full headline tables: `knowledge\SKILLS_INDEX.md`. Living inventory: `skill-forge\MANIFEST.md`.

**The daily doors:** `/aide` (the King's aide) · `/faith` (the foundation) · `/money` (the accountant) · `/save` `/recover` `/learn` `/search` (the memory loop) · `/find-skills` (best-way scout) · `/qa` + `/qa-master` + `/ship` (the gate) · `/new-project` (WAT scaffold) · `/video` `/content-engine` `/website-sales` `/upwork` `/apply` (the money engines).

## 5.2 · The Logic Tiers (0 to 100 · `_ops\SKILL_TIER_LEDGER.md`)
Every skill earns a place, like a whisper becoming stone:

| Tier | Name | How it earns it |
|---|---|---|
| T0 | Raw (a whisper) | Untested idea, kept in drafts, never shipped |
| T1 | Verified (heard) | `/find-skills` scouted it, 2+ independent sources agree |
| T2 | Consensus (witnessed) | Full multi-source consensus, maths shown, goal locked |
| T3 | Approved (the king has seen it) | Passed `/qa`, King approved, live in `commands\` |
| T4 | Foundation (carved in stone) | `/ship`'d, logged as a Trusted Stone, load-bearing |

If a T4 breaks, it is demoted honestly and re-climbs.

**The cadence layer (new 2026-07-04, same ledger):** every Logic is also tagged by WHEN it runs.
- **On-demand:** King or a session invokes it (the default, nearly everything).
- **Event-driven:** fires on a session event via hooks (SessionStart brief, PreCompact save, Stop handoff).
- **Scheduled, laptop:** Windows Task Scheduler (git sync, Notion mirror...). Dies when the laptop sleeps.
- **Cloud Routine:** Claude Code web Routines, run with the laptop OFF. The Rule #24 upgrade. Law: cloud routines carry NO keys; anything needing `.env.master` stays a laptop task.

## 5.3 · Retired skills (do not use)
- **`/studynotes`** · RETIRED 2026-07-02. It bridged to the old separate Obsidian vault, which was archived. The `.claude` brain IS the vault now. Route instead: **capture with `/learn`, retrieve with `/search`.**

---

# PART 6 · THE GATES AND THE 25 RULES

## 6.1 · The QA gate on everything (Rule #21)
Nothing reaches Production unverified: **Tested → King's approval → Trusted → Production**, scaled to stakes.
- **`/qa`** = the 8-stage pipeline gate.
- **`/qa-master`** = the adversarial inspector that runs INSIDE the Tested stage. A veteran QA engineer hired to BREAK the deliverable before King or a client hits the bug, testing for a non-technical, voice-first, phone-using owner. If it needs a developer to recover from failure, that IS a failure.
- **`/ship`** = carves the trusted stone into `_ops\TRUST_LEDGER.md`.

## 6.2 · The rules in one breath
The 25 Operating Rules live in CLAUDE.md and are the law. The spine: plan first and wait for approval (1) · explain WHY before HOW (3) · test everything (5) · save every session (6, 10) · lean spend, free-first (12, 16) · discovery + WAT before building (13) · one continuous brain across sessions (15) · consensus + proven-pattern-first, scaled to stakes (17, 22) · VISUAL storyboard before any visual build (18) · no self-contradiction (19) · sacred accuracy (20) · the QA gate (21) · love is the root, Fr Bogdan anchors faith (23) · guard King's rest (24) · the pay-grade standard: state the stack (skill + tool + prompt + logic) at the start of every non-trivial task (25).

## 6.3 · The reflex you will see every task
At the start of any task Claude flags it **trivial or non-trivial**. Non-trivial: it leads with `/find-skills` + the consensus plan + the goal, and states the stack in one line. Trivial: it says so and just does it. King's "yes" is granted only when the work carries a consensus report AND matches the goal.

---

# PART 7 · RUNNING THINGS 24/7 (deployment lanes)

Two lanes, chosen by who depends on it:

| Lane | For | Why |
|---|---|---|
| **Claude Code cloud Routines** or laptop Task Scheduler | King's OWN automations (Radar, syncs, watchers) | Free, Routines run with the laptop off, keys stay home |
| **trigger.dev / Modal** | CLIENT production (paying, must never fail) | Dashboard, retries, observability a client can be billed against |

Details: `commands\deploy.md` (the routing law + steps) · the cadence layer in `_ops\SKILL_TIER_LEDGER.md` (what runs where today) · the SKIP table in `knowledge\DEV_ZONES.md` (why trigger.dev is client-only).

What deploys is always the deterministic part (tools + workflow). The agent (Claude) stays local. Same output every time, no surprises.

---

# PART 8 · MONEY MODE · HOW MONEY FLOWS NOW

**🔴 MONEY MODE (King's call, 2026-07-02): the brain is FINISHED.** Every session defaults to the FIRST EURO (deadline: end July). No brain-building unless it directly earns or King asks. That supersedes the v8 chronology and income tables.

The live lanes (one line each · full histories in `memory\ACTIVE_PROJECTS.md`):

| Lane | The play |
|---|---|
| 🎬 Faceless Engine @30Kingdavid | Video #1 FINAL (clone voice) · warm-up to ~Jul 8 · POST DAY rec Fri Jul 10 · funnel → first euro |
| 🎬 Hook Engine product | €19 at payhip.com/b/jSCeu (€0 sales yet) · Gumroad second shelf approved |
| 🍲 The Buka (client #1) | Edit her real clips on-brand · HSE + allergens flagged |
| 💼 Olly FBA site | Paid build: consultation → spec → live preview |
| 🌐 Website Sales Engine | €99 + €39/mo · 146 demos ready (assets only, NO cold sends) |
| 💼 /upwork + /apply | Fit-score jobs, kill scams, match demos, King tap-submits |
| 🧩 DCEO lane (Amazon pays) | Work brain saves hours per shift · promotion lever · `DCEO_BRAIN\` |

**Hard walls:** ⛔ WhatsApp cold sends KILLED by King (2026-07-03, he tried before, no luck; never re-propose). Faith filter overrides money: gambling, alcohol, adult content, deception = pass. Tithe set aside from euro one.

**Four delivery metrics, every deliverable:** less time · more money · better quality · WOW factor. Miss one and it does not ship.

---

# PART 9 · DATES AND THE DAILY FLOW

## 9.1 · Guarded and time-sensitive (July 2026)
- ✝️ **Sun 12 Jul = FIRST CONFESSION · FULLY GUARDED · nothing else exists that day.** Outranks everything, including AIS LIVE.
- 📅 **POST DAY rec = Fri Jul 10** (video #1 goes live TT+IG+YT, then the phone goes DOWN for the guarded weekend).
- 🎟 **AIS LIVE Jul 11-12 = skipped live.** Recordings chased after the weekend + a Day-2 summary. The old "buy the ticket" decision from v8 is closed.
- 🎓 Tue 14 Jul = Josh graduation trip (family, protected). Robbie Tighe L4 ~Jul 14-15.
- Full roster + rhythm: `_ops\OPERATING_RHYTHM.md` (the Council's law: prayer rule on waking + sleep, one health anchor, the Aide proposes ONE move per day, King disposes).

## 9.2 · Daily flow (what actually happens each session)
1. Session opens → **SessionStart hook** briefs automatically (CLAUDE.md + rules + MEMORY.md + latest handoff). `/recover` for a deeper rebuild.
2. `/context` early · keep files under the 500-line cap.
3. MONEY MODE default: the ONE thing that moves the first euro, unless King says otherwise.
4. Non-trivial task? State the stack + consensus plan first (Rules #17 + #25).
5. Ship through the gate: Tested (`/qa` + `/qa-master`) → King's yes → `/ship`.
6. `/save` before the session ends, always (Rule #10). Handoff + memory + ACTIVE_PROJECTS badges.

## 9.3 · Where to go next
- The law: `CLAUDE.md` → `_ops\FOUNDATION_PIPELINE.md` → `_ops\CREED.md`
- The data: `knowledge\SKILLS_INDEX.md` · `memory\ACTIVE_PROJECTS.md` · `knowledge\TOOLS_CONNECTED.md` · `knowledge\DEV_ZONES.md` · `knowledge\BRAIN_WIRING.md`
- The record: `decisions\log.md` · `_ops\TRUST_LEDGER.md` · `handoffs\`

---

*End of ONBOARDING v9. Previous version (v8, 2026-05-23) lives in git history. The goal never moves: make money, build financial freedom, do it God's way. Money is the fruit, for God. Peter, not Judas.*
