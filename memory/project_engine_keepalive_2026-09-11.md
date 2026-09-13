---
name: project-engine-keepalive-2026-09-11
description: "R5.1 done 11 Sep: engine, deck and ccr restart within 5 minutes if they die, never one King holds (tools/hold.ps1). The lockout rule kept by a hold mark. Proven live: crash, hold, release."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T16:40:56.751Z
---

# The engine keepalive, with King's hold mark (R5.1, 11 Sep 2026)

**Why:** the engine was only STARTED at logon; nothing brought it back if it died. But
`after_logon_services.ps1` recorded the lockout rule: a timer must never restart what King stopped
on purpose. King ruled 11 Sep: **keepalive plus a hold mark** (the tag on the lock).

**Built (brain `ddb5a9bd`):**
- `tools/hold.ps1 engine|deck|ccr [-Reason ...]`, `-Release`, `-List`. A hold is one file in
  `~/.kd_holds` (when, who, why). Unknown names refused. A hold stops nothing: hold first, then stop.
- `tools/after_logon_services.ps1`: skips anything held (a hold beats everything), one run at a time
  (named mutex `Global\KD_AfterLogonServices`), `-DryRun` (starts and logs nothing), `-Keepalive`
  (routine lines printed, not logged, so the log holds only starts and failures).
- Task **KD_Engine_KeepAlive**, every 5 min, forever, through `tools/engine_keepalive_hidden.vbs`
  (no console flash). Declared hall C in `tools/flow_halls.py`. KD_Engine_AtLogon unchanged.

**Proof:**
- `tests/test_after_logon_services.ps1`: red (hold.ps1 missing, held engine not recognised, decision
  function missing), then green 16 of 16. Never starts or stops a process. flow_halls and Stage M
  guards 15 passed.
- Live: first run 17:25:20 result 0, no window, log untouched. **Crash:** engine killed 17:25:58,
  back 17:30:26 by the 17:30:21 run. **Hold:** held and killed 17:30:59, left down by the 17:35:21
  run. **Release:** back 17:40:25 by the 17:40:21 run, `/api/world` answering (401).

**Limits, honest:** it checks the PORT, so an engine that hangs while still listening is not caught
(a health check is its own job). Up to 5 minutes of downtime. Holds are not yet read by the other
keepalives (n8n, LOGOI, board, Remote Control).

**How to apply:** before stopping the engine, deck or ccr on purpose, `tools\hold.ps1 <name>`; take
it off after. Any restart script (like the voice switch-on) is safe: the keepalive only starts what
is down, and the mutex stops two starts at once.
