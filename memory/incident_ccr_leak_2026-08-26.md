---
name: incident_ccr_leak_2026-08-26
description: "A real leak: guarded cap-table and faith-adjacent material sent to OpenRouter through ccr on 26 Aug 2026, because the guard was never loaded. Found 10 Sep, fixed 11 Sep. Key rotated 11 Sep (68da7e716c78); closed."
metadata: 
  node_type: memory
  type: project
  originSessionId: a04f54b1-fd2d-4691-9ba2-c14de9b5d663
  modified: 2026-09-11T10:12:20.957Z
---

# INCIDENT · ccr sent guarded material to a vendor, 26 Aug 2026

**Status: CLOSED 11 Sep 2026, about 10:50.** King rotated the OpenRouter key with
`tools/rotate_openrouter_key.ps1`.
- After the rotation, `-Check` shows the new fingerprint `68da7e716c78` in the Windows variable,
  in the key store and in what LOGOI reads, and no LEAKED. ccr and LOGOI restarted on it at 10:49.
- King says he deleted the old key at openrouter.ai. That rests on his word; the script's
  "REFUSES the old key" line was not pasted.
- Still loose, his call:
  - the cold vault still seals the old key (a re-seal needs his passphrase);
  - five plaintext copies of the now-dead key are listed in `handoffs/handoff_2026-09-11_08-30_save.md`
    (delete them after asking).

## What happened

On **26 August 2026 at 22:30**, a Claude Code session running through ccr sent a request to
`https://openrouter.ai/api/v1/chat/completions` carrying material from King's own files:
cap-table terms, a client's name and faith-adjacent names, dozens of occurrences across a
451,000-character request body. It sat in the **user messages**, meaning file contents Claude
Code had read and returned as tool results. The system prompt carried none of it.

It was found on 10 Sep by a 12-agent verification of the 4D back end and confirmed directly
before it was reported: `ccr-20260826222957.log`, line 35, a `"final request"` to OpenRouter.

## Why it happened

**The guard existed and was never switched on.** ccr's config had `"CUSTOM_ROUTER_PATH": ""`,
so `tools/ccr/custom-router.js` was never loaded. Every assertion in its prover applied to
nothing. **Had it been loaded, it would have stopped this exact leak**, because it checks the
user messages and that is where the material was.

Two further faults would have defeated it even if loaded:

- Its "safe" local model, `llama3.2:latest`, cannot serve a Claude Code request (no thinking
  support), so every guarded request failed with a 400.
- ccr forces any request the guard routes into the `default` scenario, and `fallback.default`
  began with OpenRouter. So the failed local attempt walked straight to the vendor. **The
  guard's own safe choice was what sent material out.**

And `LOG_LEVEL: debug` wrote every full request body to disk, which is why the leaked material
and King's OpenRouter key were both sitting in plain text in `~/.claude-code-router/logs`.

## What was fixed, 11 Sep 2026

| fix | proven by |
|---|---|
| guard loaded: `CUSTOM_ROUTER_PATH` set | ccr restarted, PID 6008 is the only instance on :3456 |
| local model now `logos-qwen3:8b` (tools + thinking) | `ollama show` |
| `fallback.default` is local only | ccr's own cli.js logic read directly |
| `LOG_LEVEL` debug to info | config read back |
| key redacted from 5 log files, 7 occurrences | re-scan: 0 remaining, no other key shapes |
| a guarded request sent after the fix | served by **`logos-qwen3:8b` in 22 s**, and **zero** calls reached openrouter.ai. Proven in both directions. |

## What is still owed

**Rotate the OpenRouter key. This is not precautionary.** Checked 11 Sep: the key in active use (Windows user environment, `OPENROUTER_API_KEY`) begins `sk-or-v1-0352`, exactly the prefix in the leaked request header. **The key in use IS the key that leaked.** It also sat in cleartext in one stale ccr backup from 23 Aug, now redacted; all eight backups re-scanned at zero.

Redacting it from the logs removes the copy on this machine. It
does not revoke the key, and the key has already travelled to and been logged by a third party.
Same shape as the Gemini key rotated on 9 Sep and the cleartext git credential fixed the same
day. King's own rule: he creates the new key himself and Claude never sees its value.

**The data cannot be recalled.** It reached OpenRouter on 26 Aug. Their retention policy
decides what happens to it now, and that is worth one look at their terms.

## What stops it happening again

`tests/unit/test_ccr_guard_is_loaded.py`, added 11 Sep. One assertion per fault: the guard is
loaded, loaded from the live brain, cannot be overridden by a vendor in `fallback.default`, does
not write bodies to disk, and no literal key sits in the config.

**It is a live check, not a CI check, and that is deliberate.** The router is JavaScript, which
CI's path filter ignores, and the setting that broke lives in `~/.claude-code-router/config.json`,
outside the repo. CI could not have caught this leak and still cannot. So it runs on King's
machine with the rest of the suite and skips where there is no ccr.

Rotation: `tools/rotate_openrouter_key.ps1`. Run `-Check` any time to see whether the key in use
is the leaked one. Run it plain to rotate; it proves the new key before touching anything live,
restarts ccr and LOGOI, and reminds him the leak is only closed once the old key is deleted.

## The lesson, which is why this file exists

A guard is only real when its last run is checked, and this one had no last run. King's own rule
from 10 Aug, `feedback_verify_route_by_last_run`, says exactly this. **Write guards as tests, not
lists, and check that the test is actually connected to the thing it guards.** The prover passed
13 of 18 for weeks while guarding nothing at all.

Related: [[reference_anthropic_data_terms]] · [[feedback_verify_route_by_last_run]]

## The last copies deleted, 12 Sep 2026

On King's word ("re seal cold vault and delete 5 plain text"), the five plaintext copies of the
leaked key were deleted: `~/.claude-code-router/.env.local`, and `retired_env_2026-08-23/.env`
plus `.env.master` in BOTH kdbrain and the old `.claude` brain.

Checked before deleting, never assumed: every copy fingerprinted `2bcc06f645a4`, the DEAD key,
and none held the live `68da7e716c78`; every variable name in them already existed in the live
46-value store, so nothing lived only there. No key value was ever printed, only fingerprints.
After: zero key shapes remain under `.claude-code-router` or `_private`, and the live store is
untouched. The cold vault now seals that store too (`460d3623`), which it never did before.
