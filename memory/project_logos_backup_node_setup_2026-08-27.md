---
name: project_logos_backup_node_setup_2026-08-27
description: "Friend's PC as GPU-accelerated backup node for Logos engine; hardware validated, code staged, ready for Phase 1"
metadata: 
  node_type: memory
  type: project
  originSessionId: 627d3ceb-560a-4ac0-bd50-5069078fba71
  modified: 2026-09-07T11:18:45.517Z
---

# Logos Backup Node Setup · 2026-08-27

## What This Is
Friend's PC (AMD Ryzen 5 3600, RTX 2070 8GB) becomes always-on GPU-backed backup for Logos engine. Two use cases:
1. **Failover:** If laptop dies/is off, LOGOI still answers via friend's PC over Tailscale
2. **Speed boost:** Laptop sends work to friend's PC first (GPU-fast), falls back to own CPU engine if timeout

## Status (27 Aug)
**READY FOR PHASE 1.** All prep complete, code staged, hardware confirmed.

- [x] Hardware specs confirmed (nothing to buy)
- [x] Storage consolidated (D: vault + Personal OneDrive + TUD OneDrive)
- [x] Engine code staged (95 files, no secrets, 3 locations)
- [x] Transfer zip backed up (on D: vault + Personal OneDrive)
- [x] Scripts verified (setup-backup-node.ps1, start-backup-node.ps1, laptop-invoke-command.ps1)
- [x] Two artifacts published (field guide + architecture visual, both on Claude.ai)
- [x] Runbook complete (BACKUP_NODE_SETUP.md in zip, 87 lines, 5 phases)
- [x] Session context documented (two summary files, every detail)

## Hardware (Confirmed Good)
- **CPU:** AMD Ryzen 5 3600 (6c/12t)
- **GPU:** MSI RTX 2070 8GB OC (NVIDIA, CUDA-capable)
- **RAM:** 16GB DDR4 (Corsair Vengeance 2x8)
- **Storage:** 1TB NVMe Gen4 SSD
- **Motherboard:** Asus B450-class
- **PSU:** MSI 650W

**Verdict:** No purchase needed. Clears the bar entirely. RTX 2070 expected to deliver 10-20x speedup over laptop baseline (3.16 tok/s CPU-only).

## Storage Tiers (Organized)
- **D: vault (KD-LOGOS USB):** Full brain backup (8GB) + engine zip + Personal OneDrive backup (11.88GB)
- **Personal OneDrive:** Merged with TUD data, clean engine copy at `logos-engine/`
- **TUD OneDrive:** Clean engine copy at `logos-engine/` (staging, data merged into Personal)
- **Google Drive:** Skipped (sync unreliable)

## Code Staging
Transfer package: `logos-engine-for-transfer.zip` (0.73MB, 95 files)
- Location: `C:\Users\Dell\OneDrive\logos-engine-for-transfer.zip` (primary)
- Backup: `D:\logos-engine-for-transfer.zip`
- Contents: engine code, 3 scripts, runbook, Prisma schema, .env.example (no real secrets)
- Verified: ✓ No .env beyond .env.example, no .sqlite3, no API keys

## Three Scripts
1. **setup-backup-node.ps1** (one-time setup on friend's PC)
   - Installs Git, Node.js, Ollama, Tailscale
   - Pulls qwen3:8b + llama3.2:latest (~7.2GB)
   - Creates LogosBackupNode Windows user (non-admin)
   - Generates .env.backupnode with random SANDBOX_TOKEN
   - Creates Task Scheduler entries for auto-start + restart-on-failure
   - Duration: ~15 min (mostly model download)

2. **start-backup-node.ps1** (start/stop helper)
   - Three modes: default (background), -Foreground, -Stop
   - Reads .env.backupnode, ensures local-only settings override defaults
   - Starts Next.js standalone server, waits 6s, hits loopback to verify
   - Returns 401 = correct (locked, waiting for token)

3. **laptop-invoke-command.ps1** (runs ONLY on laptop)
   - Tries friend's PC first (HTTPS via Tailscale + SANDBOX_TOKEN), 180s timeout
   - Falls back to laptop's own local engine if friend's PC doesn't answer
   - Never exposes raw Ollama to network

## Network Architecture
```
King's laptop ←(Tailscale mesh)→ Friend's PC
│                                  │
├→ Local engine (loopback)         ├→ Backup engine (loopback)
└→ Local Ollama (loopback)         └→ Ollama (loopback)
```

**Auth layers:**
1. Tailscale: VPN tunnel, King's tailnet only
2. Tailscale serve: Real HTTPS cert, TLS encryption
3. Engine API: SANDBOX_TOKEN Bearer auth
4. Ollama: Bound to 127.0.0.1 only, never network-exposed (learned from 2026-08-10 audit)

## Artifacts Published
1. **Field Guide** (HTML, interactive checklist)
   - URL: https://claude.ai/code/artifact/96cc061c-be33-47b0-8241-2ecb52b32af0
   - On phone for at-the-friend's-house walkthrough
   - Phases 1-5, copy buttons for each command

2. **Architecture Visual** (SVG diagram)
   - URL: https://claude.ai/code/artifact/03c553b0-02fb-49f8-b879-58559d5f8ddb
   - Shows laptop, friend's PC, Tailscale mesh, failover logic, auth layers

## Phases (When King goes to friend's PC)

**Phase 1 (Setup):** Run setup-backup-node.ps1, save SANDBOX_TOKEN
**Phase 2 (Tailscale login):** tailscale up (use King's account, not friend's)
**Phase 3 (Serve):** tailscale serve https, note hostname
**Phase 4 (Unattended):** Enable "Run unattended" in Tailscale admin
**Phase 5 (Validate):** Reboot, measure tok/s, test failover

**Duration:** ~20 minutes total

## After Phase 1
- Create SETUP_RECORD.md on friend's PC with real values (token, hostname, password)
- Set laptop env vars: BACKUPNODE_HOST, BACKUPNODE_TOKEN
- Test laptop-invoke-command.ps1 (should answer "friend's PC")
- Turn off friend's PC, test again (should fallback to laptop's engine)
- Optional: Bookmark both hostnames on King's phone

## Security Boundary
**Never goes on friend's PC:**
- Master Brain files (memory, _ops, knowledge)
- Live API keys
- Faith files (confession prep, Fr Bogdan letters)
- Financial data

**OK on friend's PC:**
- Engine code, models, .env.backupnode (SANDBOX_TOKEN only), logs, Task Scheduler entries

**If rental ends:** Revoke device in Tailscale admin console. One click, no physical access needed.

## Stage 2 (Deferred)
Coding agents on friend's PC, with lane choice (local Qwen vs OpenRouter vs paid Claude) driven by goals.py. NOT part of this build. Waits for backup node Phase 1-5 to pass for real.

## Files This Session
- `SESSION_CONTEXT_2026-08-27.md` (summary)
- `SESSION_CONTEXT_DETAILED_2026-08-27.md` (every iota)
- Engine zip: confirmed on D: + Personal OneDrive
- Storage consolidated: 11.88GB D: backup
- Two HTML artifacts published

## SSH shell access added, 2026-08-28
King wants real SSH admin access to the backup node, not just the engine's HTTPS API. Checked
first: Tailscale's own SSH server feature does not support Windows as the target machine
(confirmed against Tailscale's own docs and an open GitHub issue), so this uses Windows'
built-in OpenSSH Server instead, tunneled over Tailscale rather than exposed to the internet.

Design: key-only (password login refused in sshd_config), logs in as the same dedicated
standard non-admin user the setup script already creates, never the friend's own Windows
account, and the Windows Firewall rule only accepts port 22 from Tailscale's own address range
(100.64.0.0/10), so it can't be reached from the friend's home network either. A brand new key
pair was generated for this one purpose only, kept separate from the existing GitHub key so the
two credentials never overlap.

Built: `scripts\setup-backup-node.ps1` now has a Step 8 that turns this on automatically, no
typing required at the friend's PC. `scripts\kdbrain_backupnode_key.pub` (the new public key,
not sensitive) and `scripts\kdbrain_laptop_ssh_shortcut.txt` (the config block for King's own
laptop) both got added to the engine repo alongside the existing three scripts.

**Re-zipped 2026-08-28, verified clean.** Fresh copy staged with the same exclusions the setup
script itself uses (node_modules, .next, .git) plus this session's own IDE dirs, the two real
`.env` files with live keys, both `.sqlite3` databases, logs, and screenshots. Checked after
staging: exactly one `.env`-style file present (`.env.example`, no secrets), zero sqlite/log/png
files, zero `node_modules`/`.git`/`.claude` directories. 94 files, 1.23MB staged, 0.33MB zipped.
Written to both `C:\Users\Dell\OneDrive\logos-engine-for-transfer.zip` and
`D:\logos-engine-for-transfer.zip`, both current as of today.

## Next Step
**Go to friend's PC, download the zip (already current), run Phase 1.**

## 7 Sep: PARKED by King's ruling
King, verbatim: **"FORGET FRIENDS PC"** (2026-09-07). LOGIC-A on the friend's PC is dropped for now, not a
failure. LOGIC-B (Oracle, live since 5 Sep, confirmed active 7 Sep: `tailscale status` active, both tailnet
doors answering 401 = locked and awake) is the cloud node. Do not re-propose the friend's PC unless King
reopens it. The zip, scripts and runbook above stay valid if he ever does.

## 29 Aug
This backup node is now **LOGIC-A** of the KD Robot three-node plan: friend's PC primary, an Oracle
always-free VM (LOGIC-B) as fallback. Nothing else here changes; the setup stays Phase 1 as written
above. Full plan and King's rulings: [[project_kd_robot_three_nodes_2026-08-29]]. The five backup-node
files in the engine repo (three scripts, the public key, the SSH shortcut with its placeholder hostname)
are still untracked on purpose; they get committed with Stage 4b.

## 2 Sep, date confirmed
King: **"I am doing Friends PC setup on Friday"** (2026-09-04). The plan's own window was "Mon 31 Aug
2026 or Fri 4 Sep 2026"; Monday passed without it, Friday is now the confirmed date, 2 days out from
tonight.

Same evening, a background security review flagged `scripts\setup-backup-node.ps1`: the fresh
`SANDBOX_TOKEN` was written to `.env.backupnode` with default inherited ACLs, readable by any local
account on the friend's machine (not King's own PC, so this matters more, not less). Fixed before
Friday: the install root (`$InstallDir`) is now locked with `icacls` right after creation (service
user, SYSTEM, Administrators only, everything created under it after that point inherits the
restriction), and `.env.backupnode` gets its own explicit ACL on top as defense in depth. Matches the
lockdown pattern the script already used for the SSH directory in Step 8. Untracked still, commits
with the rest of Stage 4b on Friday.

**Estimate for Friday itself (not yet measured, grade S):** winget installs ~5-10 min, pulling the two
models (qwen3:8b ~5.2GB, llama3.2 ~2GB) ~5-20 min depending on the friend's internet, npm install plus
Prisma generate/migrate a few minutes, Task Scheduler and SSH setup under a minute; script total
roughly 20-40 minutes. Then interactive steps after (Tailscale login, `tailscale serve`, the SSH host
entry on King's own laptop, one reboot to prove both scheduled tasks and SSH come back on their own):
another 10-15 minutes plus reboot time. All from `BACKUP_NODE_SETUP.md` and the script's own step
list, none of it timed live yet; redraw solid once Friday actually runs it.

**Zip verified stale and refreshed, 2 Sep.** King asked to verify before Friday. It was: written 28 Aug
06:33, before `af7fcb0` (Stage 1, prompt records) and tonight's `13a1974` (the token ceiling
enforcement, a real money-safety feature). Rebuilt from the current engine HEAD with the same
exclusions the 28 Aug session used (node_modules, .next, .git, IDE dirs, every real .env file,
both sqlite3 databases, logs), verified three ways before trusting it: the staged tree checked
file-by-file for secret-shaped paths, the finished zip's own entry list re-checked the same way after
compression (not just the staging folder), and the exclusion list itself checked against what
actually sits at the engine root (`.env`, `.env.klarnow`, `.env.klarnow.bak-pre-clientkey`,
`klarnow.sqlite3`, `v0.sqlite3`, all four confirmed excluded, zero hits in the finished zip).
319 files staged, 2.86MB, zipped to 1.24MB. Both copies replaced (`OneDrive\logos-engine-for-transfer.zip`,
`D:\logos-engine-for-transfer.zip`), current as of 2 Sep 23:40. Staging folder deleted after.
