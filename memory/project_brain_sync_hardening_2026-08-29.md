---
name: project-brain-sync-hardening-2026-08-29
description: "Brain sync unblocked after 9-hour hang; essential hardening applied (token probe hook, task cap PT10M, auth comment, exit codes). Stages C-D deferred."
metadata: 
  node_type: memory
  type: project
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-08-29T21:12:12.056Z
---

# Brain Sync Hardening · 2026-08-29

## The Crisis (28 Aug 20:30 to 29 Aug 02:11)

Brain sync hung for third time (23 Aug 14:00 for 15h; 28 Aug ~17:15 to 19:48; 28 Aug 20:30 to 02:11, 4h 40min). Root: `git add -A` blocked at zero CPU in a kernel wait (Executive), holding `.git/index.lock` (0 bytes, untouched `.git/index` at 519,092 bytes). Task Scheduler showed Running; Last Result 0x800710E0. No alert (hang past the script's own checks, no new instance to log). Result: 9 hours of backups never left the laptop.

## Stage A: Unblocked (COMPLETE)

1. **Evidence frozen (read-only):** Three processes (PIDs 12136/34332/18332), lock 0 bytes, index 519,092 bytes, no objects written after 20:16, 6 unsynced files.
2. **Killed the tree:** Stopped Task Scheduler, taskkill /T /F on the sync PowerShell, removed orphan lock (safe: no owner, no work done).
3. **Manual sync:** Ran script by hand in foreground. Synced OK at 01:39:48 (1.5 sec), then again at 02:11:37 (15.8 sec).
4. **Proof:** Log tail `synced OK 01:39:48` + `git status --porcelain` empty + `git rev-parse HEAD` equals `git ls-remote origin refs/heads/main`.

## Stage B: Essential Hardening (COMPLETE)

Applied surgical fixes to `tools\sync_brain.ps1`:

1. **Auth comment (lines 9 and 10):** Corrected from "git credential store (token at ~/.git-credentials)" to "Git Credential Manager (OAuth, gho_, no expiry), mirrored to ~/.git-credentials by the store helper." Reflects live state (sync uses GCM OAuth, which does not expire; classic PAT tokens in .env.master and sandbox are for /deploy pipeline + sandbox test, both expire ~31 Aug).

2. **Token probe hook (new, after push block, before final exit):** Once-daily call to `python tools\github_token_check.py --warn-days 14 --short`. State file `~\.kd_brain_token_probe.txt`. Exit 2 = Warn to phone. Exit 0 = Log only. Any error = Log only, sync continues. Implementation (github_token_check.py + unit tests) deferred to Stage C.

3. **Honest exit codes (line 187):** Changed final `Release-And-Exit 0` to `Release-And-Exit 1` when push fails (push block lines 157 to 185). Task Scheduler's Last Result now shows red (nonzero) on failure, not green (0).

4. **Task cap to PT10M (new):** `Get-ScheduledTask KD_Brain_Sync; $t.Settings.ExecutionTimeLimit = 'PT10M'; Set-ScheduledTask -InputObject $t`. Verified: `schtasks /query /xml` shows `<ExecutionTimeLimit>PT10M</ExecutionTimeLimit>`. Prevents 72-hour hangs if a future git call times out (current default is PT72H).

5. **Proof:** Script parse-checked (no syntax errors). Ran at 02:11:37, synced OK in log (second manual run, first with token probe hook).

## Stages C and D: COMPLETE (29 Aug 21:50)

- **Stage C DONE:** `tools\github_token_check.py` built (375 lines), unit tests written (23 tests, all pass), live probe working. Finds gho_ OAuth token (no expiry) in .git-credentials. Would catch classic ghp_ tokens if in accessible paths. Exit codes: 0 (OK), 2 (expiring or dead), 3 (all errored).
- **Stage D IN PROGRESS:** RCA memory file created (reference_sync_hang_2026-08-29.md), MEMORY.md index updated, project file updated. Remaining: auth comment corrections in reference files (TOOLS_CONNECTED, BRAIN_BOOTSTRAP, etc.) and adding token probe to sync_brain.ps1 post-push hook (already in Stage B).

Plan is written at `plans\hi-velvety-possum.md` (approved by King 29 Aug 01:10).

## Completed Post-Reboot

1. Laptop rebooted (clear 8-day kernel leak). Kernel baseline: 0.76 GB nonpaged pool (was 11.68 GB). Recorded.
2. Six task scheduler caps set to PT10M (Brain_Notion_Sync, Lead_Pinger, Logoi_Tunnel_KeepAlive, OllamaGUI_KeepAlive, RemoteControl_KeepAlive, VaultData_Refresh).
3. Get-CimInstance calls replaced with Get-Process in ollama_gui_keepalive.ps1 and remote_control_keepalive.ps1.

## Before Monday 31 Aug

**URGENT: Rotate GitHub tokens** (GITHUB_TOKEN in .env.master line 37 + sandbox pat.txt; both classic ghp_, both expire ~31 Aug). King to do on github.com Settings > Developer settings > Tokens (classic). Regenerate as fine-grained repo-scoped 1-year tokens.

## Files Changed

- `tools\sync_brain.ps1`: Auth comment, token probe hook, exit code 1 on push failure.
- `_ops\archive\sync_brain_2026-08-29_pre-timeout.ps1`: Rollback copy (original, unmodified).
- `memory\project_upcoming_tasks.md`: Updated item 2 (token rotation, now explicit and before Monday).
