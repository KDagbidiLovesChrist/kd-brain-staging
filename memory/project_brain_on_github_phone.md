---
name: brain-on-github-phone
description: "King's .claude brain is on private GitHub (kd-brain) + auto-syncs every 15 min + works from his phone via Claude Code web. Route A. Keys kept OFF cloud."
metadata: 
  node_type: memory
  type: project
  originSessionId: 29b464e9-6981-4bf0-a91c-f8108976e0cf
  modified: 2026-08-01T03:48:21.982Z
---

# Brain on GitHub → Claude from King's phone (Route A) · LIVE 2026-06-16

King wanted to use Claude with his full setup **from his phone**. Done via **Route A (cloud)**:
his brain lives in a private GitHub repo, Claude Code on the web loads it, he drives it from his phone.

## ✅ Username RENAMED (2026-07-27): kinglovesJessie → `KDagbidiLovesChrist`
- King renamed the GitHub account himself in web settings (he was offered `kdagbidi` but chose **`KDagbidiLovesChrist`** — confirmed live via the API `/user` login). Repo name stays `kd-brain`.
- Laptop side all updated same day: 16 live brain files swept to the new name, `origin` remote re-pointed to `https://github.com/KDagbidiLovesChrist/kd-brain.git`, and the username inside `C:\Users\Dell\.git-credentials` updated (same PAT, still valid — never print it).
- Handoffs + archives keep the old names on purpose (historical records). `kdagbidi.com` mentions in old files = an unrelated DOMAIN King declined in June — never touch those.
- ⚠️ Freed names `kinglovesjessie` + never-used `kdagbidi` are claimable by strangers; GitHub's old-URL redirect dies if that happens — everything live already points at the new name, so no exposure.
- Hand-step still open: **King re-prints Joshua's successor letter** (it names the account) before sealing.
- ✅ **Vercel renamed too (same day):** account username `kinglovesjessie` → **`kdagbidiloveschrist`** (King's hand-step in vercel.com/account; Vercel forces lowercase, so this is the lowercase twin of the GitHub name). Team `king-david-s-projects2`, all projects, domains and the CLI token were untouched and verified working. 9 live files swept.

## What's live now
- **Private repo:** `KDagbidiLovesChrist/kd-brain` (GitHub). **Private**, only collaborator = `KDagbidiLovesChrist`,
  **zero secret files inside** (verified 3×). Holds the lean brain: CLAUDE.md, memory/, commands/,
  knowledge/, brand_assets/, tools/, plugins/, skills/, PIPELINE.md, settings.json (1,035 files).
- **`.claude` is now a git repo** (`main` branch, remote `origin` → kd-brain). Credential = a GitHub
  **PAT (repo scope)** stored at `C:\Users\Dell\.git-credentials` (OUTSIDE the repo, never committed).
  NOTE: PAT has no `read:org`, so `gh auth login --with-token` fails, we used the GitHub **API + git**
  directly (create repo via API, push with token URL). gh CLI is NOT logged in.
- **Auto-sync robot:** `tools\sync_brain.ps1` + Windows scheduled task **`KD_Brain_Sync`** (every 15 min
  while laptop on). Two-way: commits local changes → `git pull --rebase` (phone/cloud changes) → push.
  Secrets can never sync (the repo `.gitignore` is **default-deny**: blocks everything, allows only the
  brain folders, re-blocks all `.env`/token/credential/db/media). Log: `C:\Users\Dell\.kd_brain_sync.log`.
- **Phone access works:** King is on **Claude Code web (claude.ai/code), Max plan**, kd-brain connected;
  already ran sessions ("Who am I?", "Kitchen island visualization"). Talk in **plain English** (his
  `/commands` don't auto-register in the cloud, just ask naturally; Claude reads the skill files as SOPs).

## The `.gitignore` design (important · don't loosen)
Default-deny allowlist at `C:\Users\Dell\.claude\.gitignore`: `/*` ignores everything, then `!/CLAUDE.md`,
`!/memory/`, `!/commands/`, `!/knowledge/`, `!/brand_assets/`, `!/tools/`, `!/plugins/`, `!/skills/`,
`!/PIPELINE.md`, `!/settings.json`; then re-blocks `*.env`, `credentials.json`, `token*.json`, `*.db`,
`*.key`, `*.pem`, `node_modules/`, `.vercel/`, and heavy media (`*.mp4/*.mov/*.zip/*.webm`). LESSON:
in a whitelist gitignore, use plain `*.mp4` (matches any depth), NOT `**/*.mp4` (didn't match here).

## Decisions locked
- **Route A only** (cloud). **Route B (Remote Desktop / Tailscale RDP) explored but DROPPED**, laptop
  IS ready for it (Win 11 Pro, RDP on, Tailscale up `100.103.239.114`) if he ever changes his mind.
- **Scope = lean brain only.** Big projects stay on the laptop (Website Builder = 6.8 GB, too big for
  GitHub). New builds are born in the cloud; bring a specific existing site over slimmed-down only on request.
- **KEYS KEPT OFF THE CLOUD (King's choice, max-safe).** Claude Code web has **no sealed secrets vault**,   only a "visible" Environment-variables box that warns *"don't add secrets."* So King chose to keep all
  keys in `.env.master` on the laptop. Consequence: from the phone he can think/plan/write/**build**, but
  **deploy + image-gen happen at the laptop** until/unless he adds keys later.

## How to operate it
- **Laptop → cloud/phone:** automatic (KD_Brain_Sync every 15 min). Or manual: `git -C C:\Users\Dell\.claude push`.
- **Cloud/phone → laptop:** the robot pulls every 15 min. Or manual: `git -C C:\Users\Dell\.claude pull`.
- **Re-verify privacy/secrets anytime:** GitHub API on `repos/KDagbidiLovesChrist/kd-brain` (private:true) +
  `/git/trees/main?recursive=1` (no .env/token/credential paths).

## NEXT (optional, when King wants)
- **Laptop-off deploys:** add only low-risk, easily-rotated keys to the Claude Code web env box,   `VERCEL_TOKEN` (deploy), `KIE_AI_API_KEY` + `GEMINI_API_KEY` (images), `PERPLEXITY_API_KEY`. Keep the
  sensitive ones (Supabase service-role, Google, payment) OFF. He can delete/rotate any in 1 min.
- **Later project:** cheap Telegram/WhatsApp chat-assistant wired to his **Obsidian** vault (Nate-style,
  n8n, cheap model), reuse the `/studynotes` Obsidian bridge. See [[project-upcoming-tasks]].

## 🆕 2026-06-27 · phone-branch sweep added (phone work was getting STRANDED)
PROBLEM found: Claude Code on the **phone** saves each session to its own **`claude/...` branch that NEVER merged into main**, so the auto-sync (which only syncs `main`) left that work stranded on GitHub, invisible to the laptop brain. Caught it when King's first-Confession lesson + a finance log + a John's-prayer script were missing locally (they were on `origin/claude/confession-liturgy-explanation-...` and `origin/claude/loan-payoff-plan-...`). **FIX: added a branch-sweep step to `tools\sync_brain.ps1`**, after the pull, it fetches all `origin/claude/*` branches and CLEAN-merges any with unmerged commits into main; anything that would conflict is left safe on its branch + logged (phone work is **never lost**). Tested live: swept the confession (4 commits) + loan-payoff (3 commits) branches in and pushed. **Idempotent** (a merged branch is 0-ahead next run → skipped). From now on phone sessions land in the brain on their own. (3 other `claude/*` branches were empty/already-merged.)

## 🆕 2026-07-31 · sync audit + stranded 07-14 branch recovered + WARN alerts wired
King asked "is everything in sync?" Audit: laptop == GitHub, robot healthy, 19/20 phone branches merged.
The 20th (`claude/idea-brainstorming-2btvht`, 07-14 grad-day voice capture = the **scavenge-proven-assets
rule**) sat STUCK 17 days on one MEMORY.md line conflict, with the robot warning into the unread log every
15 min (second demonstration of the 07-16 RCA alert gap). Hand-merged (kept compact index, added the rule
line to MEMORY.md + RULES_INDEX.md), pushed, branch now 0-ahead. **Then the alert gap was CLOSED (King-approved):**
`sync_brain.ps1` now pushes its 3 sync-critical WARNs (pull conflict · stuck branch · push fail) to the
ntfy phone channel, throttled 1/day per unique problem (`~\.kd_brain_sync_alerted.txt`); PROVEN live (test
ping received, duplicate throttled, cycle synced OK). DCIM warns stay log-only (non-blocking). Details:
[[reference-sync-break-2026-07-16]]. Note: `tools\token-dashboard` always shows " M" in status — it's a
submodule of Nate's repo with local doc edits; NOT a sync issue, leave alone.

## 🆕 2026-08-01 · CLOUD sweep robot — phone branches merge into main 24/7, laptop OFF
King asked for GitHub↔local sync "24/7 automatically" without keeping the laptop on. Clarified the model:
GitHub IS the cloud (nothing to "upload"); the phone already writes it instantly; the 15-min robot only
mirrors the laptop's own copy. The ONE laptop-off gap was the branch-sweep (phone `claude/*` branches only
merged when the laptop robot ran — the 07-14 branch sat 17 days). **FIX (King-approved): GitHub Action
`.github/workflows/sweep-phone-branches.yml`** — runs on GitHub's servers on every push to `claude/**`
(+ daily 06:00 UTC cron catch-all + manual dispatch). Mirrors `sync_brain.ps1` step 3 exactly: clean merges
→ push main; conflicts → abort, branch left SAFE, ntfy ping to the phone. Auth = built-in GITHUB_TOKEN only
(NO PAT, keys-off-cloud intact; GITHUB_TOKEN pushes can't re-trigger workflows, no loops). €0, ~1 min/run.
**QA'd live both paths (2026-08-01):** clean probe branch merged into main in <1 min by the Action (run
success, branch 0-ahead); deliberate conflict branch left safe (main untouched, branch ahead-1) + ntfy ping
received. Test branches + probe file cleaned up. Also proven: August CI free minutes are BACK (runs execute
again after the July burn). Laptop robot untouched — stays as idempotent backup. Caveat: cloud conflict
pings are NOT day-throttled (one per triggering run; real use = one per phone session push).
A second cloud (Drive/Dropbox holding the repo) was considered and REJECTED — file-sync tools corrupt git
repos and split the truth. Plan: `plans\will-cloning-my-github-zazzy-plum.md`.

Plan file: `plans\i-want-to-connect-curious-adleman.md`.
