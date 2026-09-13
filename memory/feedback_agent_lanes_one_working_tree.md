# One working tree, three agents: each door gets its own folder

**Set 10 September 2026**, when King put Claude, Codex and PowerShell in one VS Code window and
asked to run them together while the infrastructure synced.

---

## The rule

| door | owns | never touches |
|---|---|---|
| **Claude, the chair** | `memory/` `knowledge/` `_ops/` `handoffs/` `tests/` | `engine/` |
| **Codex, hard building** | `engine/` | `memory/` `knowledge/` `_ops/` `handoffs/` |
| **ccr, the free floor** | bulk and repetitive work, declared first | `engine/` `memory/` |
| **shell** | his own hands, no lane | |

**Never two agents in the same file at the same time.**

---

## Why, and it is not tidiness

**Git-level collisions are already solved.** `tools/sync_brain.ps1` holds a named system mutex and
detects a stale `index.lock`, both added 26 August after a live deadlock that blocked the sync for
an hour at zero CPU.

**Work-level collisions are not solved, and cannot be.** Two separate facts combine:

1. **`KD_Brain_Sync` runs `git add -A` every 15 minutes** and commits whatever is in the tree. If
   Codex is halfway through a refactor when it fires, that half lands in a commit.
2. **All the doors share ONE working tree**, not branches. Two agents editing one file means one
   silently overwrites the other. Git never sees a conflict because there is nothing to merge.

The lanes make collisions impossible by construction rather than by care, which is the same
principle as every other gate in this brain: **a scanner, not a hand-picked list; a boundary, not
a promise.**

---

## Where it is enforced

**In the terminal profiles** (`.vscode/settings.json`), so each door announces its own lane on the
line before the agent starts. That is the only place an agent reliably reads before acting.

**Not by `cwd`**, deliberately. Pinning a profile's working directory to `memory/` was considered
and rejected: Claude Code needs the repo root for `CLAUDE.md`, its hooks and its tools, so a
narrowed `cwd` would break the session to enforce a rule the greeting already carries.

---

## The lanes are not new

They are what his own profile labels already said. The chair is judgement, contracts, faith and
architecture. Codex is web interfaces, TypeScript and the engine. ccr is bulk, cheap and
repetitive. **This only writes down the folder each of those descriptions implies**, so an agent
does not have to infer it.

---

## 11 Sep addendum: the mutex does not cover a session's own git writes
- **What happened.** A Claude session committed at 09:14:58, 24 seconds before the 09:15 sync.
  The sync's `git pull --rebase --autostash` then failed, and `git rebase --abort` left a stale
  `.git/rebase-merge` holding only an autostash.
- **The effect.** Every later cycle logged "pull conflict" and skipped its push, from 09:15 to
  09:47. It exited 0, and the phone rang once only, because alerts are deduplicated per day.
- **The rule:** keep deliberate git writes (commit, push, fetch) out of the sync minutes (:00,
  :15, :30, :45, plus about a minute after each). After any git write, check that
  `.git/rebase-merge` is absent and that `origin/main...main` is `0 0`.
- **The safe clear** for a stale folder holding only an autostash is `git rebase --quit`. It moves
  no commit and keeps the autostash in the stash list. Look inside the folder first.
- **The lasting fix** is the stuck-git alarm in the push-scan design
  (`_ops/logs/rulings_2026-09-11/push-scan_judge.md` 4.4).

---

**Related:** [the two economies and the doors](../knowledge/HARNESS_MAP_2026-09-08.md) ·
[sync hang RCA](reference_sync_hang_2026-08-29.md) ·
`tools/sync_brain.ps1` (the mutex and the lock guard) · `.vscode/settings.json` (where it lives)
