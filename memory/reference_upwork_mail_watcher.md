---
name: reference-upwork-mail-watcher
description: "The local Windows scheduled task that auto-checks King's Gmail for Upwork/freelance jobs, scores + drafts them, and pushes his phone on a GO. How it works, how to pause/check."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c768dc5e-a40d-4160-a733-867e96fc4a54
---

# Upwork Job Watcher (local, automatic)

Built 2026-06-09. King wanted "automatically check my mail and when a relevant job comes in, do your thing." The built-in cloud `/schedule` routines CAN'T do this (they run in Anthropic's cloud with no access to his local Gmail token, demo library, drafts folder, or phone-push, and min interval is 1h). So it runs LOCALLY on his laptop instead.

## What it is
- **Script:** `C:\Users\Dell\.claude\tools\upwork_mail_watcher.py`
- **Schedule:** Windows Task Scheduler task **"KD Upwork Watcher"**, every **30 min**, runs `pythonw.exe` (no console window). Runs whenever the laptop is on + logged in (NOT a 24/7 server).
- **State file:** `tools\.upwork_watcher_state.json` (processed Gmail IDs + daily Claude-call counter, so nothing is re-processed or spammed).

## What it does each run
1. Reads new Gmail (`newer_than:1h`, skips already-processed IDs).
2. Python hard-prefilter (`JOB_HINTS` regex), if nothing job-like is new, it **exits without calling Claude** (costs nothing).
3. For each candidate, calls **Claude Haiku** (key from `Documents\Newsletter Demos\.env`) to: decide if it's really a job, score 0-100 vs King's green-light bar, kill scams, pick the best proof demo from `knowledge\demo_library.md`, and draft a proposal (King's voice, zero em-dashes, NO price, no fabricated claims).
4. GO (score >= 60) -> appends a block to `drafts\upwork_applications_<today>.md` and **pushes King's phone** (`tools\push_kd.py`). No GO -> silent.
5. King reviews + submits on Upwork himself. The watcher NEVER logs into Upwork.

## Best way to feed it (closed loop)
King should turn on **Upwork saved-search EMAIL ALERTS** for his top lanes (n8n, AI automation, AI agent, chatbot, landing page, Shopify, Next.js/web app). Those alert emails land in Gmail -> the watcher scores + drafts them automatically. He can also just forward any job to his own Gmail. Searches/criteria live in [[project-upcoming-tasks]] and `commands\upwork.md`.

## Manage it
- **Check:** `Get-ScheduledTaskInfo -TaskName "KD Upwork Watcher"` (LastRunTime / LastTaskResult 0 = ok).
- **Run now:** `Start-ScheduledTask -TaskName "KD Upwork Watcher"`.
- **Pause:** `Disable-ScheduledTask -TaskName "KD Upwork Watcher"`. Resume: `Enable-ScheduledTask`.
- **Test manually (shows log):** `python C:\Users\Dell\.claude\tools\upwork_mail_watcher.py`.
- **Cost:** fractions of a cent per new job email (Haiku); empty checks are free. Daily call cap = 200.

## Proven
Test run 2026-06-09 00:48 correctly classified King's own "HOW TO SEND" emails as NOT jobs (score 0), no false push, quiet exit. Pipeline (Gmail -> prefilter -> Claude -> draft -> push) verified end to end.
