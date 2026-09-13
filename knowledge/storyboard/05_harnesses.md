# 5 · The harnesses · the tack, not the horse

**A model is the horse. A harness is the tack: the saddle and reins that let the horse carry you
and touch your things. You own several sets of tack, and mixing the two up is how money leaks
and files travel where they should not.**

```
MODEL     the brain that thinks       Fable, Opus, Astra, Gemini, qwen
HARNESS   the body with hands         the editor, the terminal, git, your files
```

---

## 5.1 Why the difference matters

**They fail differently, so they are rescued differently.**
- **A model running out** is fixed inside your engine, automatically: the router walks the lane to
  the next rung.
- **A harness running out** is fixed by you, with one command and GitHub. Push, open the next door,
  pull, carry on.

**You watched the split happen today.** The same horse, `gpt-6-astra`, was ridden with two sets of
tack on 11 September:
- the Codex panel in VS Code (the engine's database lock fix, commit `a0c2061`);
- Codex's command line, driven by Claude (the voice lane).

Same model, different tack, and each one asked for your permission in a different way.

---

## 5.2 The tack you own, measured today

| harness | version | horses it reaches | how it is paid | can you govern it |
|---|---|---|---|---|
| **Claude Code** | 2.1.267 CLI, 2.1.268 in VS Code | Claude only: Fable 5.1, Opus 5, Sonnet 5, Haiku 4.5 | your Claude plan | **no**, it talks straight to Anthropic |
| **Codex** | 0.153.4 | GPT: `gpt-6-astra` as the lead, effort `medium` since 17:11, with Luna and Terra helpers (part 6.5) | your ChatGPT plan, the 20 USD monthly budget you enforced on 9 September | **no**, it talks straight to OpenAI |
| **ccr** | 2.0.0, on your laptop at port 3456 | OpenRouter's `gemini-3.8-flash` on five routes, the local `llama3.2:1b` on one | per call, on your OpenRouter key | **yes**, the one harness with your guard in the path |
| **Gemini CLI** | 0.59.0 | Gemini | no login chosen yet | **no** |
| **Antigravity** | installed, the app and the IDE | Gemini, some Claude models, Nano Banana | Google's free bars | **no** |
| **Copilot CLI** | 1.0.83 | several, depending on the plan | plan unknown | **no** |
| **Ollama** | 0.34.0 | qwen3:8b, llama3.2 3b and 1b | free, your electricity | **yes**, nothing leaves the laptop |

**Not on this laptop:** Kiro (the work laptop only, your ruling of 8 September), Hermes, and `agy`.

---

## 5.3 The rule that follows: most of your doors cannot be governed

Your own words on 8 September: **a harness window talks straight to its vendor.**

Claude Code, Codex, Antigravity and Copilot each send your words directly to their own company.
Nothing of yours sits in between to check them, count them or refuse them. The only limit is that
account's own cap.

**You govern exactly two things:**
- **your engine,** through its spend gate, its travel gate and the lanes table;
- **ccr,** through its guard.

That is why your rule from the same day holds: **subscriptions carry the interactive work, and API
keys carry only the automated engine work.**

---

## 5.4 ccr: the one bridge, and why it is not free

ccr is a small gateway on your laptop. `ccr code` opens Claude Code's own window but sends the work
through ccr's routes instead of to Anthropic.

- **Five of its six routes go to OpenRouter's `gemini-3.8-flash`, which is paid per call.** Only the
  background route goes to the free local 1B model.
- **Its door greeting called it the free lane, and it is not.** ✅ **Ruled 12 September: option B**,
  keep the paid routes and fix the wording, on the evidence that it has cost **USD 0.00** on the
  current OpenRouter key. The ladder in `commands/doors.md` and `HARNESS_MAP_2026-09-08.md` now
  both say paid on 5 of 6.
- **Its guard is loaded now.** On 26 August the guard existed but was never switched on, and
  guarded material reached OpenRouter (`memory/incident_ccr_leak_2026-08-26.md`). It was fixed on
  11 September and proven: a guarded request reached OpenRouter zero times.
- **Claude Code does not go through ccr.** `ANTHROPIC_BASE_URL` is unset, so a plain `claude` spends
  your Claude plan directly and ccr sits unused.

---

## 5.5 Where the record and the laptop disagree

- **Codex effort.** It read `high` in `~\.codex\config.toml` earlier today, against a 9 September
  record of `medium`. Settled the same evening: `medium` since 17:11, with cheaper helpers doing the
  legwork (part 6.5).
- **Gemini.** The CLI was installed on 9 September, but no login was ever chosen. Separately, your
  Gemini API balance was below zero (AI Studio, 15:38 today). You topped it up the same afternoon,
  and the voice lane answered through Gemini at 17:04.
- **Copilot.** Installed, with its plan still unknown since 8 September.

---

## REAL TODAY

| | |
|---|---|
| **real** | Claude Code; Codex on your ChatGPT plan with a 20 USD cap, and driven from the command line for the first time today; ccr with its guard loaded; Ollama 0.34.0 |
| **half built** | ccr works, but it is paid on five routes while its door says free; the Gemini CLI has no login; Copilot has no known plan |
| **zero** | Hermes and `agy`; Kiro, by your ruling, lives only on the work laptop |

⚠️ **Only two of your doors can be governed: your engine and ccr.** Every other window talks
straight to its vendor, bounded only by that account's cap.

**Proof:** commands run on 11 September:
- `claude --version` 2.1.267;
- `codex --version` 0.153.4, and `codex login status` "Logged in using ChatGPT";
- `ccr version` 2.0.0, and its `config.json` routes read by name, with `CUSTOM_ROUTER_PATH` set;
- `ANTHROPIC_BASE_URL` unset, for both the user and the process;
- `gemini --version` 0.59.0, with no auth type in its settings;
- `copilot --version` 1.0.83;
- `ollama --version` 0.34.0;
- Antigravity folders present under `AppData\Local\Programs`.

**Next:** [6 · The door ladder](06_door_ladder.md)
