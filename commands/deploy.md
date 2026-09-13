# /deploy · Deploy Automations to Run 24/7

You are King David's deployment guide. When /deploy is triggered, help him take a trusted
workflow and tool set and deploy it to run automatically, no manual trigger needed.

## ⚖️ THE ROUTING LAW (read FIRST · 2026-07-04)
Pick the lane by WHO depends on it, before anything else in this file:

| Who it serves | Lane | Why |
|---|---|---|
| **King's OWN / personal automations** (Radar, syncs, watchers, newsletter for himself) | **Claude Code cloud Routines** (free, runs with the laptop OFF) or **laptop Windows Task Scheduler** (needs the laptop on; fine when the job needs local files/keys) | Free, lean-spend (Rule #12). Cloud Routines carry NO keys; anything needing `.env.master` stays a laptop task or gets prepped in cloud + executed at laptop. |
| **CLIENT production** (a paying client, must NEVER fail) | **trigger.dev / Modal** | Dashboard, retries, observability a client can be billed against. |

What runs where today = the cadence layer in `_ops\SKILL_TIER_LEDGER.md`. Why trigger.dev
is client-only = the SKIP table in `knowledge\DEV_ZONES.md`. The trigger.dev steps below
apply to the CLIENT lane (and remain the reference for Task Scheduler on the personal lane).

## What This Skill Does
Guides King David through the full deployment pipeline:
Local test → GitHub push → trigger.dev or Windows Task Scheduler → runs forever.

This is the WAT principle in action: W (workflow) + T (tools) deploy to the cloud.
The A (agent = Claude) stays local. What runs in the cloud is deterministic code,
not an AI deciding things on its own.

---

## STEP 1: IS THE WORKFLOW TRUSTED?

Before deploying anything, it must be battle-tested. Ask King David:

1. Have you run this workflow at least 5 times successfully?
2. Did it handle any errors gracefully (or did Claude fix them during runs)?
3. Did the output look exactly right every single time?

**If no:** Do not deploy yet. Run it more. Fix any remaining issues. Trust = consistency.
**If yes:** Move to Step 2.

---

## STEP 2: CHOOSE YOUR DEPLOYMENT PATH

Present two options based on what's set up:

### Option A: Windows Task Scheduler (Local · No GitHub Needed)
Best for: King David's personal laptop. Newsletter runs locally on schedule.
Requirement: Laptop must be on and connected at scheduled time.

```
HOW IT WORKS:
  Windows Task Scheduler → runs Python script → at set time → automatically
  (Newsletter sends itself every Monday at 8am as long as laptop is on)
```

Steps:
1. Confirm the Python script runs cleanly with: `python run_newsletter.py`
2. Run the schedule setup: `python newsletter-demos\tools\schedule_setup.py` (from the brain root `C:\Users\Dell\.claude`; laptop working copy also at `C:\Users\Dell\Documents\Newsletter Demos\tools\schedule_setup.py`)
3. Choose schedule: Daily / Weekly (Monday) / Custom
4. Confirm task is registered in Windows Task Scheduler
5. Test: set schedule to 2 minutes from now, wait, confirm it fires

### Option B: trigger.dev (Cloud · Runs 24/7 Without Your Laptop)
Best for: Production. Newsletter runs in the cloud even when laptop is off.
Requirements: GitHub account + trigger.dev account (both free).

```
HOW IT WORKS:
  GitHub repo → trigger.dev reads tools\ → runs on schedule → sends newsletter
  (Tools are deterministic code, they do the same thing every time, no AI needed)
```

Steps:
1. Install git: `winget install Git.Git` (King David runs this once)
2. Create GitHub account at github.com (if not done)
3. Create repo: `git init` → `git add .` → `git commit -m "Initial commit"` → push
4. Create trigger.dev account at trigger.dev (free)
5. Connect GitHub repo to trigger.dev
6. Set schedule: every Monday at 8am
7. Set environment variables in trigger.dev dashboard (API keys from .env)
8. Test: trigger a manual run in trigger.dev dashboard
9. Confirm: check email, newsletter arrived

---

## STEP 3: ENVIRONMENT VARIABLES

The tools use API keys stored in .env locally. In the cloud, these go into the
platform's environment variables section (not .env files, those don't deploy).

For trigger.dev:
- Go to: Project → Environment → Variables
- Add each key from your .env file:
  - `ANTHROPIC_API_KEY` = your Claude API key
  - `PERPLEXITY_API_KEY` = your Perplexity API key
  - `GMAIL_ADDRESS` = your Gmail
  - `GMAIL_APP_PASSWORD` = your Gmail app password

---

## STEP 4: VERIFY DEPLOYMENT

After deploying, always verify:
1. Trigger a manual run from the dashboard
2. Check the output, did the newsletter send correctly?
3. Check the logs, any errors?
4. If errors: diagnose here in Claude Code, fix the tool, re-deploy

---

## DEPLOYMENT STATUS TRACKER

Ask King David which projects are currently deployed:

| Project | Local (Task Scheduler) | Cloud (trigger.dev) | Status |
|---------|------------------------|---------------------|--------|
| Newsletter | ⬜ Not set up | ⬜ Not set up | Pending |
| Lead Scraper | N/A | N/A | Manual only (Fiverr) |
| Website Builder | N/A | N/A | Manual only |

Update this table as deployments are completed.

---

## WHAT GETS DEPLOYED vs WHAT STAYS LOCAL

```
DEPLOYS TO CLOUD:             STAYS LOCAL:
├── tools\*.py                ├── Claude Code (the agent)
├── workflow\*.md             ├── CLAUDE.md (the brain)
├── .env variables            ├── memory\ (King David's context)
└── requirements.txt          └── skills\ (the /commands)

The agent (Claude) is NOT deployed.
Only the workflow recipe + tool scripts run in the cloud.
This makes it deterministic, same output every time. No surprises.
```

---

## TRIGGER PHRASES
When King David says any of:
- "deploy the newsletter"
- "schedule this to run automatically"
- "make this run 24/7"
- "set up trigger.dev"
- "automate the schedule"

→ Start this workflow from Step 1.
