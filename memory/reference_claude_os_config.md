---
name: reference-claude-os-config
description: "Claude OS config state after the 2026-06-16 tune-up: which MCPs run, the spend dial, the single-file Stop hook, the status line, and the gh-token to-do (2026-06-16), PLUS the 2026-07-11 FULL-CONTROL grant King authorised (bypassPermissions + broad allow + deny seatbelt + whole-profile reach). Read before changing settings.json or the auto_handoff hook."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 5383c6c1-ddc1-4ee2-b16d-e48e9a4c102c
---

# Claude OS config · tuned-up state (2026-06-16)

Full tune-up of `~/.claude/settings.json` + the Stop hook + the memory index. What changed and why:

## settings.json
- **MCP servers running:** `playwright`, `firecrawl`, `n8n-mcp` only.
- **Removed** `brave-search` + `github` MCPs, both held placeholder keys
  (`your-brave-api-key-here`, `your-github-token-here`) and failed every startup. Brave was
  redundant (Firecrawl + Perplexity + built-in WebSearch cover search); the GitHub MCP was unused
  (deploys go through `gh`/`git` CLI + Vercel). Re-add only if genuinely needed.
- **Spend dial = "optimise what is best":** kept `model: opus` + `effortLevel: xhigh` (his
  builds/designs/copy are the product), set `verbose: false` (display noise, no quality cost).
- **Permission allowlist** expanded (additive, safe only): `vercel`, `git status/diff/log/add`,
  `python`, `node`, fewer prompts when he works hands-free by voice/phone. Existing allows kept.
- **Status line** added → runs `tools/statusline.py`.

## Status line · tools/statusline.py
Prints under every prompt: `KD · <model> · FOCUS: <live next move> · €0 → first sale · God's way`.
Pulls FOCUS live from the first NEXT item in `memory/project_upcoming_tasks.md`. Edit the MONEY /
GOAL constants at the top of the script as things change. Never crashes (all lookups wrapped).

## Stop hook · tools/auto_handoff.py
- **Was** writing a new timestamped `handoff_<date>_auto.md` EVERY turn → had created **2072 files
  / ~42MB** in `handoffs/`. Now writes a single rolling **`handoff_latest_auto.md`** (overwritten).
- Deleted the 2072 disposable auto packets; **all 130 real `*_save.md` handoffs kept**. `/recover`
  is unaffected (it finds the latest `*_save.md`).

## MEMORY.md
- Was 30.9KB (over the 24.4KB cap → only partial load). Rewrote every entry as a true one-liner
  (all links preserved) → **21.0KB**, full index loads every session again.

## Manual to-do for King (interactive · Claude can't do it)
- **`gh auth login`** to renew the GitHub CLI token (expired 2026-06-16). Only needed before the
  next `git push` / `/deploy`; Vercel-only deploys don't need it.

## FULL CONTROL grant (2026-07-11) · King explicitly authorised
King asked, twice and plainly, for the AI to have **full control over the laptop system** ("Yes I
want you to have full control"; "I still have final say and can remove your control anytime").
Verified the mechanism first (deny beats allow, honoured even in bypass mode; built-in circuit
breaker still stops `rm -rf ~` / `rm -rf /`) then edited `settings.json`:
- **`permissions.defaultMode: "bypassPermissions"`** → zero prompts, full control.
- **Broad allow added:** `Bash(*)`, `PowerShell(*)`, `WebFetch(*)`, `WebSearch(*)` (fallback in case
  the known bug makes `defaultMode` not stick on a fresh session; if prompts return next session it
  is that bug, not a fault, and **Shift+Tab** flips back to full control).
- **`permissions.deny` seatbelt (7 rules, beat everything):** `rm -rf ~`, `rm -rf /`, `rm -rf /*`,
  `mkfs:*`, `Format-Volume:*`, `Clear-Disk:*`, `diskpart:*` → catastrophic disk-wipe blocked even
  in full-control mode.
- **`additionalDirectories`** now leads with `C:\Users\Dell` (whole profile reach), old entries kept.
- **The line that stays (behavioural, not in settings):** still STOP and get King's yes before
  spending money, sending/posting, deleting what I did not make, or publishing. Peter, not Judas.
- **King's off switches:** Shift+Tab (instant, per session) · say "remove full control" → revert or
  set `disableBypassPermissionsMode` (hard lock) · close the session. King has final say, always.
- ⚠️ Current MCPs in settings = `playwright` + `n8n-mcp` only (firecrawl noted above is no longer
  wired; re-add when a task needs it). Model line = `claude-fable-5[1m]`.

See [[feedback-lean-spend-llama-routing]] (the spend rule this honours) and
[[feedback-dont-overcomplicate]] (kept it lean, no output-style file, no removed allows).
