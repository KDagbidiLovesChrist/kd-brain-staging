# The Harness Map · what is on the Dell, what each door reaches · read 2026-09-08

Source: a read-only inventory (3 sweeps, a designer, an adversarial checker, 152 tool uses) plus
direct probes the same day. Every key below is named and length-checked only; no value was ever
read, and none appears here. Companion ruling record:
[[project_kd_robot_stage6_console_2026-09-06]] (the 8 Sep section).

## The two layers, because they are constantly confused
A **model** is the brain that thinks (Fable, Astra, Gemini, qwen). A **harness** is the body with
hands (editor, terminal, git). They fail differently, so they are rescued differently: a model
running out is fixed INSIDE the engine by the router walking the lane, automatically; a harness
running out is fixed by one command plus GitHub, push, open the next door, pull, carry on.

## Installed on the Dell, verified 2026-09-08

| Door | State | Models it reaches | Best for | Quota readable by script? |
|---|---|---|---|---|
| **Claude Code** 2.1.263 (CLI, VS Code ext, desktop app) | installed | Claude only: Fable 5.1, Opus 5, Sonnet 5, Haiku 4.5 | the chair, judgement, legal, terminal coding, the brain itself | partly: plan bars in-app only; local spend from the statusline JSON or OTel |
| **ccr** 2.0.0 (gateway on 127.0.0.1:3456) | installed, **routes dead** | ollama, openrouter, nvidia, logoi, gemini | the everyday free door, via `ccr code` | OpenRouter yes, by its own key endpoint; the rest no |
| **Antigravity** 2.12.2 app + 2.5.5 IDE | installed twice | Gemini 3.8/3.7/3.6 Flash, 3.1 Pro, Claude Sonnet 4.6, Opus 4.6, Nano Banana 2 | visual work, image mockups, a free second opinion | in-app only; its `agy` CLI is not installed |
| **Codex** 0.153.4 | binary present, **not on PATH** | GPT. Configured **`gpt-6-astra`, effort `xhigh`** (corrected 9 Sep; the first write said `gpt-5.6-sol` at `ultra` and both were wrong) | web interfaces, hard architecture | no; balance on OpenAI's own page only |
| **Copilot CLI** 1.0.81 | installed, **plan unknown** | Claude (incl. Fable 5.1), GPT (incl. Astra), Gemini, Grok, Kimi, per plan | a multi-model fallback when other bars are spent | yes, through the GitHub billing endpoint, if a plan exists |
| **Ollama** 0.33.2 | installed | qwen3:8b, llama3.2 (3b, 1b), nomic-embed | rung one: faith, private work, bulk, the floor | no quota. It is free |

Not installed on the laptop: **Gemini CLI**, **Cursor**, **`agy`**, **Kiro** (work laptop only, by
King's 8 Sep ruling). **Hermes Agent installed 13 Sep, on Oracle (LOGIC-B)**, not the laptop, and
reached from the phone through a Telegram bot, not through this laptop's own door ladder.

Supporting tools: gh 2.92.0 (**signed out**), node v24.15.0, python 3.12.10, git 2.54.0, uv 0.11.13.

## Provider keys present, by NAME only
Filled: ANTHROPIC, OPENAI, DEEPSEEK, GEMINI, OPENROUTER, NVIDIA, PERPLEXITY, plus TAVILY,
FIRECRAWL, ELEVENLABS, APIFY, GITHUB and infrastructure entries. Blank: VAPI, BRAVE, NTFY topic.
How the store is located: `tools\logoi_keys.py` holds the ordered `STORE_PATHS`; only the one in
the profile root exists. Never quote a value into any file, ever.

## Faults found on 2026-09-08, none yet fixed
1. **ccr's routes point at retired models.** `default`, `think`, `webSearch` and `image` point at
   `gemini-2.0-flash` and `longContext` at `gemini-1.5-pro`; only `background` (ollama llama3.2:1b)
   names a live model. **Honest nuance (9 Sep):** the routing is confirmed from the config, but that
   those two Gemini models are retired is read from Google's own list, not from a failed run.
   `ccr code` has never actually been executed. Run it once before relying on it as the daily door.
2. **A LITERAL secret in ccr's config**, not a probable one (upgraded 9 Sep). Parsed
   programmatically, printing name, length and whether the value starts with `$`: openrouter and
   nvidia carry environment references, gemini carries a 53-character literal. That is an incident
   to rotate, not a question to defer. The value itself was never read.
3. **Codex is uncapped**, `auth_mode = apikey` on pay as you go, at **`gpt-6-astra` and `xhigh`
   effort** (corrected 9 Sep from a misread of `gpt-5.6-sol` at `ultra`). That makes it worse, not
   better: Astra is 10 and 50 USD per million against Sol's 4 and 20. King ruled 8 Sep: cap the
   account and drop the effort first, then judge a subscription on a week of real numbers.
4. **`harness_switch.py` writes the same handoff file the Stop hook rewrites every turn**, so its
   record is erased within minutes (seen live: a 09:25 note gone by 13:27). It needs its own file.
5. **Claude Code is not going through ccr** (no base URL override set), so plain `claude` spends the
   Claude plan directly. The gateway runs unused on 3456.

## What a script can and cannot read
**Readable:** which doors exist; local health (Ollama, LOGOI, the deck, ccr); whether LOGIC-B is up,
by a tailnet ping plus a health check run over SSH on the box itself, since its 3000 and 11434 are
CLOSED on the tailnet address and only 22 is open; OpenRouter credit; Copilot usage; Hermes
insights; Claude Code's own local spend.
**Not readable:** Claude plan bars, Antigravity bars, Gemini free tier, OpenAI balance, NVIDIA,
DeepSeek. For these the cockpit can only say which door fits, never how much room is left.

## The door ladder, King's ruling 2026-09-08
1 `ccr code` (**paid on 5 of 6 routes**, corrected 12 Sep 2026; only `background` is free, on the
local `llama3.2:1b`. King's ruling: keep the paid routes, fix the wording. Measured spend on the
current OpenRouter key: **USD 0.00**) · 2 Claude Code (plan already paid) · 3 Codex (on a paid GPT plan) ·
4 Antigravity (free Google bars) · 5 Copilot CLI (if a plan exists) · **6 Hermes, corrected 13 Sep:
real, on Oracle, via Telegram, on gemini-3.8-flash, NOT free and NOT on Ollama as this ruling first
assumed** · 7 Ollama direct, the floor, cannot run out.
Two economies: **subscriptions for interactive harness work, API keys only for automated engine
work.** The status tool recommends the next door; it never launches one.

## Open questions for King
Which Antigravity install and which Google account he actually uses; whether the ccr gemini key is
a literal secret (he opens the file); whether any Copilot plan is active; which OpenAI org owns the
6 Sep key and whether a cap exists; whether Astra is switched on for his accounts.
