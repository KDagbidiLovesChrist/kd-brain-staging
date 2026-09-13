---
name: reference-n8n-local-setup
description: How to run/import/execute/reset the FREE local n8n (localhost:5678) + the cloud-trial-expired lesson
metadata: 
  node_type: memory
  type: reference
  originSessionId: 3953f959-08c8-4087-b1c1-4a7a4165f4d1
---

# n8n · Local (free) vs Cloud (paid), and how to drive it

**Golden rule (lean spend, see [[feedback-lean-spend-llama-routing]]):** use the **free local n8n** on King's laptop. The **n8n Cloud** workspace `kingdavidai.app.n8n.cloud` was a TRIAL that **ended 2026-05-31** ("Max from n8n" email) → it locks you out and costs money to reopen. Don't pay for cloud unless a client specifically needs cloud hosting.

## Local n8n facts
- Installed npm-global: `C:\Users\Dell\AppData\Roaming\npm\n8n.cmd` (v2.20.9). Runs at **http://localhost:5678**.
- Start it (long-running, run in background): `n8n start`. Set `$env:N8N_DIAGNOSTICS_ENABLED="false"` first.
- It has its OWN owner login (email + password, stored locally). **No email recovery**, local has no SMTP (`smtpSetup:false`). If the password is lost, reset it (below), don't hunt for a reset email.

## Reset a forgotten local login
1. Stop the server: find PID on 5678 (`Get-NetTCPConnection -LocalPort 5678 -State Listen`) → `Stop-Process -Id <pid> -Force`.
2. `n8n user-management:reset`  → "Successfully reset the database to default user state." **Workflows survive** (only users wiped).
3. `n8n start` again → refresh localhost:5678 → it shows **"Set up owner account"** (fresh email+password, no verification). Confirm via REST: `GET http://localhost:5678/rest/settings` → `data.userManagement.showSetupOnFirstLoad` should be `True`.

## Import a workflow JSON via CLI
`n8n import:workflow --input="<file.json>"`. Two gotchas that bit us:
- The JSON **must have a top-level `"id"`** field (the UI auto-adds one, the CLI does not → `SQLITE_CONSTRAINT: NOT NULL ... workflow_entity.id`). Add e.g. `"id": "ai-assistant-demo"`.
- File **must be UTF-8 with NO BOM**. PowerShell `Set-Content -Encoding utf8` adds a BOM → `Unexpected token '﻿' ... is not valid JSON`. Write with `[System.IO.File]::WriteAllText($p,$s,(New-Object System.Text.UTF8Encoding $false))`.
- Re-importing with the same `id` UPDATES the stored copy.

## Run a workflow headlessly (prove it works)
`n8n execute --id=<workflowId> --rawOutput`  (the v2 `--file` flag is GONE; runs by id from the DB).
- If the server is already running you hit **"Task Broker's port 5679 is already in use"** → add `$env:N8N_RUNNERS_ENABLED="false"; $env:N8N_RUNNERS_BROKER_PORT="5699"` before the command. It then runs on the JS runner and prints full `runData` (each node's output) + `status:"success"`.

## The AI Customer Assistant demo
- Clean shareable file (placeholder key, give THIS to clients): `Website Builder\n8n-demos\ai-assistant-n8n.json`.
- 4 nodes: Manual trigger → Set (customer message) → HTTP POST to `api.anthropic.com/v1/messages` (model `claude-haiku-4-5-20251001`, RIVELLA Plumbing system prompt) → Set (extract `content[0].text`).
- Verified LIVE 2026-06-03: ran via local n8n engine, Claude answered the boiler question in ~2.3s, ~150 tok in / 142 out (fractions of a cent). Also live as a hosted page: `ai-assistant-demo-blond.vercel.app`.
- For PAID client builds: put the key in n8n **Credentials** (encrypted), never typed into the node, so the key doesn't travel when the workflow is exported.
- Real Anthropic API key lives at `Documents\Newsletter Demos\.env` (`ANTHROPIC_API_KEY=sk-ant-api03-...`). `.env.master` does NOT have it. `.claude\.credentials.json` is the Claude Code OAuth token (sk-ant-oat), not a general API key.
