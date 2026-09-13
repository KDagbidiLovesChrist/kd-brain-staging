---
name: incident-windows-update-rollback-2026-09-11
description: "The 11 Sep reboot installed Windows 11 25H2 (build 26220 to 26200.9445) and put four of that morning's system settings back, including the LEAKED OpenRouter key in the Windows setting. Files were untouched. All four repaired and proven the same day."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T11:46:42.728Z
---

# INCIDENT: a Windows feature update undid the morning's system settings (11 Sep 2026)

**Status: repaired and proven, 11 Sep 12:45.**

## What happened
King rebooted at 11:33 after the key rotation and option B. Windows installed "Windows 11,
version 25H2" during that reboot (update history: 11 Sep 11:35, succeeded). The build went from
26220 before to 26200.9445 after.

After sign in, four settings changed earlier that morning were back to their earlier state:

| Setting | After the update | Harm |
|---|---|---|
| Windows user variable `OPENROUTER_API_KEY` | the LEAKED key (`2bcc06f645a4`) | ccr and the engine read it, and the key was deleted at OpenRouter |
| Task `KD_Logoi_Tunnel_KeepAlive` | enabled again | it pushed a new LOGOI login link to the phone at 12:03 |
| Task `KD_Engine_AtLogon` | deleted | ccr, the engine and the deck never started |
| Startup `KD Vault HUD.lnk` | pointing at the old brain again, beside a `(1)` copy pointing at kdbrain | the old-brain HUD opened at logon |

**Files were NOT rolled back.** The key store, `engine/.env` (`LOGOS_LOCAL=1`), the engine DB
(kd-faceless) and `_private/logoi_auth.json` all kept the morning's changes. So the damage was
exactly the settings Windows keeps outside ordinary files: the registry environment, the task
store and one Startup shortcut.

## How it was found
R1 of the post-reboot plan checks the running state, not the files:
- ports 3456, 3000 and 3200 were down;
- the engine task was not found;
- the tunnel task read Ready;
- `rotate_openrouter_key.ps1 -Check` showed LEAKED on the Windows line only.

**A test that reads files would have passed.**

## How it was repaired (all proven)
1. **The key:** copied from the key store into the Windows setting, never shown. `-Check` shows
   `68da7e716c78` three times.
2. **The tunnel:** the task was disabled again and cloudflared stopped. The 2 new login links (11:41
   and 12:03, both unused, 8 uses left) were cancelled. The session secret was left alone because
   nothing was used.
3. **The engine task:** `KD_Engine_AtLogon` was re-registered exactly as before (logon plus 1
   minute, battery allowed, 10 minute limit, `tools/after_logon_services.ps1`) and started at
   12:45:02. It was the first real run ever, with result 0. `~\.kd_after_logon.log` shows:

   | Service | Started | Listening |
   |---|---|---|
   | ccr | 12:45:10 | 3456 at 12:45:19 |
   | engine | 12:45:11 | 3000 at 12:45:24 |
   | deck | 12:45:11 | 3200 at 12:45:37 |

   All three started after step 1, so they read the new key.
4. **The shortcut:**
   - `test_no_stage_m_leftovers.py` went red naming `KD Vault HUD.lnk`.
   - The old-brain shortcut was deleted and the kdbrain copy renamed.
   - The test went green, 6 of 6.

Only OPENROUTER_API_KEY was affected among the key names shared by the store and the Windows
setting (checked by fingerprint), and only KD_Engine_AtLogon was missing from the 25 registered
tasks (checked against `tools/flow_halls.py`).

## The lesson
**After any Windows update, re-check the system settings, not just the files.** In practice:
- `tools/rotate_openrouter_key.ps1 -Check`;
- the KD task list diffed against `tools/flow_halls.py`;
- the tunnel task state;
- `test_no_stage_m_leftovers.py`.

**The lasting fix, on the R5 list:** a self-check at logon.
- It compares the key store with the Windows setting by fingerprint.
- It diffs the live tasks against `tools/flow_halls.py`, including their Disabled state.
- It rings the bell once, with a job name and a verdict only, if either has drifted.

Related: [[incident_ccr_leak_2026-08-26]] · the rotation that this undid ·
`handoffs/handoff_2026-09-11_10-45_save.md`.
