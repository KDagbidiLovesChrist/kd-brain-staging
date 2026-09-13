---
name: project-codex-token-setup-2026-09-11
description: "Codex ran out of its ChatGPT Plus allowance mid-task on 11 Sep because it ran every step on gpt-6-astra at effort high with no helpers. King: set token management up, he will upgrade the GPT plan. Set up 11 Sep: Astra at medium as lead, Luna and Terra helpers, two profiles. Live helper proof owed."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T19:46:09.434Z
---

# Codex token setup (11 Sep 2026)

**Why:** Codex hit its Plus limit mid-task on 11 Sep (voice fix, back at 19:27), and Claude had to
finish it. King asked "I thought he would delegate to other gpt models not just Astra", then:
*"Get the token management set up accordingly codex shouldn't be running out like that I'll upgrade
my gpt account."*

**What was found:**
- `~/.codex/config.toml` had `model = "gpt-6-astra"`, `model_reasoning_effort = "high"`, and no
  helpers. The 9 Sep record ([[project-doors-and-cost-2026-09-09]]) says it was dropped to medium,
  so something set it back to high after 9 Sep. Suspect: the model picker in the Codex app or the
  VS Code ChatGPT extension (pid 6152, running since 11:41), which writes this file.
- Codex never delegates by itself. OpenAI's docs: "Current local Codex releases spawn agents after
  a direct request or applicable project or skill instruction."
- **OpenAI's Codex pricing page (read 11 Sep), messages per 5 hours:**

  | plan | Astra | Sol | Terra | Luna |
  |---|---|---|---|---|
  | Plus, 20 USD | 5 to 45 | 10 to 100 | 25 to 200 | 250 to 2,000 |
  | Pro, 100 USD | 25 to 225 | 50 to 500 | 125 to 1,000 | 1,250 to 10,000 |
  | Pro, 200 USD | 100 to 900 | 200 to 2,000 | 500 to 4,000 | 5,000 to 40,000 |

  Fast mode uses the allowance faster. Helpers use their own tokens, so a spawn is not free.

**What was set (backup `~/.codex/config.toml.bak-2026-09-11-tokens`):**
- `config.toml`: Astra stays the lead (his 10 Sep org chart, [[project-model-org-chart-2026-09-10]]),
  effort **high to medium**; `[agents]` default helper `gpt-5.6-luna` at medium, at most 3 at once.
- `~/.codex/agents/`: **scout** (Luna, low, read-only), **bulk** (Luna, medium), **builder**
  (Terra, medium, test first). Each forbids keys, commits, pushes, restarts and live data.
- `~/.codex/AGENTS.md`: the lead keeps planning, design and final checks; legwork goes to the
  helpers by name; small jobs done alone; zero dashes; red then green.
- Profiles: `codex -p deep` (Astra, high, hard jobs only), `codex -p everyday` (Terra, medium).

**Proof:** every file parses; `codex debug prompt-input` (free, no model call) exit 0 and shows the
AGENTS.md rules and the spawn tools. **LIVE PROOF, 19:41 on 11 Sep** (King: "Do what you want"): a
read-only `codex exec -s read-only` job told to have its scout do the reading. Its session files in
`~/.codex/sessions/2026/09/11/`: the lead `rollout-...T19-41-34-...` on `gpt-6-astra` effort
`medium` (the lowered setting took effect), the helper `rollout-...T19-41-53-...` on
`gpt-5.6-luna` effort `low`, carrying the scout's own instructions. Answer correct (42 prove
files, 2 with LOGOS_PROVER_RUN, checked against the tree), engine unchanged, 29,613 tokens, 60 s.
**How to check a run later:** each rollout file's `turn_context` holds `model` and `effort`.

**The same evening, with the helpers:** after the 19:27 reset Codex did the helper proof (29,613
tokens), the fabrication checker fix (engine e19ea89), the money workspace triage and paper-trading
stage 1, and then stage 2 (90,809 tokens), before hitting the Plus limit again at 20:44 ("try again
at Sep 12th, 2026 12:41 AM"), with stage 2 already complete. Far more work per window than the
afternoon, when one fix on Astra at high used it up. Plus is still tight for an evening of builds:
evidence for the upgrade question, which King deferred until after the 28th (money).

**King asked (19:40) whether to run Codex in the VS Code extension instead.** Same engine, same
allowance (the extension runs `codex.exe app-server` on the same `~/.codex`). Claude's advice: work
from Claude's briefs via `codex exec` (one pass, no chat re-sending the conversation, saved
settings honoured); use the extension to watch or steer by hand, after reloading VS Code (its
process dated from 11:41, before the 17:11 settings change), and mind that its picker rewrites
`config.toml`.

**How to apply:** Claude's Codex briefs name the helpers for the legwork. If effort shows high again,
check the app's picker first. Undo: copy the backup over `config.toml`.
