# Reference · The Cheap Lane (run Claude Code on a cheap/free model for grunt work)

*Set 2026-06-22. Goal: a SECOND, cheap Claude Code lane for bulk/simple/non-client work, while the
normal `claude` command stays on **Opus** (the money-lane). Lesson from @emilsystems clip + GLM 5.2 study.*

## ✅ ACTIVATED 2026-07-10 (Option A, $0) · smoke test PASSED
- **Use it:** open any terminal → `ccr code` → Claude Code runs on the FREE local model. Main `claude` untouched (Opus).
- **Live stack:** `ccr` = `@musistudio/claude-code-router` **PINNED @2.0.0** + Ollama + **qwen3:8b** (5.2 GB, local, free).
- **Config:** `C:\Users\Dell\.claude-code-router\config.json` (Providers: ollama → localhost:11434/v1/chat/completions; Router default/think/background = `ollama,qwen3:8b`).
- **Proof:** `ccr code -p "Reply with exactly: CHEAP LANE OK"` → replied `CHEAP LANE OK` (2026-07-10).
- ⚠️ **Gotcha 1: do NOT upgrade ccr to v3.** v3 became a desktop app (SQLite config, UI-driven); the simple CLI + config.json flow is v2. If ccr says "No available models", check the version.
- ⚠️ **Gotcha 2: the model must support THINKING.** Claude Code sends thinking requests; qwen2.5-coder was rejected by Ollama ("does not support thinking") and was replaced with qwen3:8b (thinks natively). qwen2.5-coder deleted (disk was 88% full).
- Reminder unchanged: cheap lane output must ALWAYS be verified (small local model, fine for grunt, weak for hard tasks).

## 🔒 THE ONE HARD RULE (do not break)
**NEVER put `ANTHROPIC_BASE_URL` in your global `~/.claude/settings.json`.** That would secretly route
**ALL** your Claude Code, including client/money work, to the cheap model and tank quality (against the
"optimise what is best" rule). The cheap lane must be a **separate command / per-terminal only**.
- Normal money-lane = type `claude` (untouched, still Opus).
- Cheap lane = a separate launcher (`ccr code`, or `cheap_lane.ps1`).

## Option A · FREE & LOCAL (claude-code-router + Ollama)  ← truly $0
Weaker model (qwen2.5-coder). Good for: rough drafts, boilerplate, summaries, throwaway scripts. NOT
client builds. King already has Ollama installed. One-time setup on the laptop:
```powershell
ollama pull qwen2.5-coder                      # grab a free local coder model
npm install -g @musistudio/claude-code-router  # the proxy (28k★, MIT)
ccr ui                                          # opens a web UI → add Ollama provider + qwen2.5-coder
```
Then to USE it (separate from normal claude):
```powershell
ccr code            # launches Claude Code on the local free model
# inside, /model ollama,qwen2.5-coder  to switch; run `ccr restart` after config edits
```
Cost = $0. Quality = laptop-level (fine for grunt, weak for hard tasks).

## Option B · NEARLY-FREE & STRONG (GLM 5.2 via Z.ai)  ← recommended cheap lane
~5× cheaper than Opus, much stronger than the local model. Needs a Z.ai GLM Coding Plan key (~$10/mo or
pay-as-you-go). Use the safe per-terminal launcher `tools/cheap_lane.ps1` (does NOT edit global settings):
```powershell
$env:ZAI_API_KEY = "your_zai_key"      # from z.ai dashboard
.\tools\cheap_lane.ps1                   # launches Claude Code on GLM for THIS terminal only
```
(Endpoint used: `https://api.z.ai/api/anthropic`. Or run `npx @z_ai/coding-helper` for guided setup.)

## When to use which lane
- **Opus (`claude`)** → all client/money/complex/flagship work. Default. Never cheap out here.
- **Cheap lane (`ccr code` / GLM)** → bulk, simple, repetitive, throwaway, non-client tasks. **Always
  verify its output** (esp. GLM, it overclaims success). See `feedback_lean_spend_llama_routing.md`.

## Status
Scaffold + launcher committed to the brain (syncs to laptop). Activation = the one-time laptop install
above (npm/ollama for A, or a Z.ai key for B). Claude can't run those installs from the cloud, King runs
them once on the laptop, then it's a permanent second lane.

## UPDATE 2026-08-23: CCR moved off Ollama, NVIDIA NIM added, real gotchas found

**The default quietly changed.** `~/.claude-code-router/config.json`'s Router (default/background/think)
now points to `openrouter,z-ai/glm-5.2:free`, not `ollama,qwen3:8b`. Ollama is still listed as a provider
but nothing routes to it day to day. This is faster and free, keep it as the default.

**NVIDIA NIM added as a THIRD provider** (King's ask, accepted the data-policy risk knowingly, see
`[[project_logoi_agent]]`). `deepseek-ai/deepseek-r1`, the original pick, is DEAD, a raw call 404s, it's
gone from NVIDIA's live catalog. Corrected to `openai/gpt-oss-120b` for the CCR/Claude Code coding lane.
**Verdict after real testing: don't use it as the default.** At xhigh effort it hung past 2m37s on a
one-line prompt and had to be cancelled; even at low effort it stayed slow. NVIDIA's free tier is a
backup for when OpenRouter is rate-limited, not a daily driver. If reaching for NVIDIA, prefer the
smaller `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning` (verified 1.6s direct, and confirmed ALSO free
via OpenRouter itself) over the 120b model.

**A second CCR provider now exists too:** `logoi` (`http://127.0.0.1:5056/v1/chat/completions`,
built by a parallel session same night), pointing CCR straight at LOGOI's own socket
(`logos`/`logos-raw`). Not routed to by default, available via `/model logoi,logos-raw`.

**⚠️ REAL GOTCHA, costs real confusion if forgotten: `/model` inside a `ccr code` session does not
just switch that one window.** It overwrites the GLOBAL `~/.claude/settings.json` `"model"` field as
the default for ALL new Claude Code sessions, including plain `claude` (the money lane) elsewhere. Used
carelessly, this leaves `claude` trying to open with a router-style string like
`"nvidia,openai/gpt-oss-120b"` that means nothing to real Anthropic, and it visibly fails
("Using [that string] (from .claude\settings.json)" in the banner). **After any `/model` experiment in
a ccr session, check `grep -n '"model"' ~/.claude/settings.json` and put it back to `"sonnet"` if it
changed.** This bit King directly on 23 Aug, caught and fixed mid-session.

**OpenRouter free tier rate-limits transiently.** Saw repeated `z-ai/glm-5.2:free ... 429 ...
temporarily rate-limited upstream` errors, unrelated to anything broken here, a shared free pool
getting busy. `retry_after_seconds` in the error is usually accurate; if not, wait longer and retry,
don't assume the setup itself is broken.

**Live OpenRouter free-model catalog checked directly against their own `/v1/models` API on 23 Aug**
(not blog posts): 18 free models, several of them NVIDIA's own (Nemotron line) available for free
THROUGH OpenRouter too, a second free path to NVIDIA models without the separate NVIDIA key at all.
`logoi_envoy.py`'s OpenRouter fallback tier was widened from 4 to 7 models the same day for exactly
this reason, see `[[project_logoi_agent]]`.

## ✅ ccr LANES SET AND VERIFIED (2026-08-23) · measured, not inferred

**All seven ccr route keys had been pointing at `logoi,logos`**, the brain-aware lane with TF-IDF
retrieval and the grounding gate. `logoi_openai.py` documents `logos-raw` as the one "For ordinary
coding work", so every coding request was being given brain context it did not want and a gate built
for client claims. That hurt accuracy as much as speed.

### The final config, every number measured through ccr on :3456

| lane | value | measured |
|---|---|---|
| `default` | `nvidia,openai/gpt-oss-20b` | 4.7s code, **0.8s tool_use YES**, 128k window |
| `background` | `ollama,llama3.2:1b` | 2.6s, LOCAL so conversation content never leaves |
| `think` | `nvidia,nvidia/nemotron-3.5-lightning-30b-a3b` | 17.1s, most thorough (506 tokens) |
| `longContext` | `nvidia,openai/gpt-oss-20b` | 3.3s at >60k, needle found at 95,295 tokens |

⚠️ `webSearch` and `image` are set to gpt-oss-20b but **neither actually works**, see below.

### THE TRAP THAT BIT THREE SEPARATE TIMES: max_tokens too low

Reasoning models spend the output budget on thinking BEFORE any answer. With a small `max_tokens`
they return **HTTP 200 with empty content**, which looks exactly like a broken model:

- `ollama,qwen3:8b` at 400 tokens: 148.6s, **zero chars**. Not broken, starved.
- `nvidia,gpt-oss-120b` at 256 tokens: 32.5s, **empty**. Then 504 at 400 tokens.
- `gpt-oss-20b` needle test at 60 tokens: **failed**. At 120 tokens: correct at 95k context.

Claude Code sends thousands, so this is a TEST-HARNESS artefact, not a deployment one. **Never judge
a model on a small max_tokens.** An earlier round of this work wrongly concluded "NVIDIA times out"
and "qwen3 returns nothing" purely from a 400 cap.

### Facts worth keeping

- **OpenRouter is a dead end on this account.** `is_free_tier=true, usage=0`, so every paid slug is a
  hard 402 at billing and the free slugs give 429/404/403. `z-ai/glm-5.2:free` 429s from a shared
  upstream pool. Do not retry other `:free` slugs; the blocker is billing and data-policy gates.
- **`gpt-oss-120b` vs `gpt-oss-20b` is night and day**: 120b timed out (504 after 302s), 20b answers
  in 3.7s. Only 120b had been wired.
- **`logoi,logos-raw` (37s) beats `ollama,qwen3:8b` (148s, empty) on the SAME model**, because LOGOI
  strips the `<think>` block. Local coding should always go through logos-raw.
- **Context ceiling is discoverable from the error**: at ~170k, NVIDIA returns
  `max_tokens must be at least 1, got -37023`, i.e. limit minus prompt. That puts gpt-oss-20b at
  roughly 131k tokens.
- **A Router entry naming a model NOT in that provider's `models` array does not resolve.** Declare
  the model on the provider in the same edit, or every call fails.
- **ccr needs the API keys in ITS OWN process env.** Config holds `$OPENROUTER_API_KEY` /
  `$NVIDIA_API_KEY` placeholders which ccr expands from its environment. Both are set in
  `HKCU:\Environment`, so a ccr started from a shell that predates them gets a literal `$VAR` and
  **401s**. Start it from a fresh shell, or inject from the registry.

### Still broken, deliberately not papered over

- **`image`: there is NO vision model anywhere.** `qwen3:8b`, `llama3.2:1b`, `llama3.2:latest` and
  the NVIDIA lanes are all text-only. This ccr build DOES route images (an image agent rewrites
  `body.model` to `Router.image`), so pasting a screenshot into Claude Code will fail. Fixing it
  means `ollama pull llama3.2-vision` (~7.9GB) or a cloud vision model.
- **`webSearch` fires on Anthropic's SERVER-SIDE `web_search` tool**
  (`tools.some(h => h.type?.startsWith("web_search"))`), which NVIDIA cannot perform. The lane is set
  so it does not fall through oddly, but it will not actually search the web.
- ⚠️ **IP: `default` on NVIDIA means King's code leaves the laptop.** For Klarnow engine work, where
  ownership is unsigned and contested, that is an outbound disclosure. Switch to `logoi,logos-raw`
  for those sessions and accept ~37s.

### One command to protect the IP boundary: `tools/logoi_lane.py`

King chose NVIDIA as his default coding lane for speed and said he would switch to local by hand for
Klarnow engine work. That plan relied on him REMEMBERING, and the cost of forgetting is his own
engine source on someone else's servers. So the switch is one command, not a JSON edit:

```
python tools/logoi_lane.py            show the current lane
python tools/logoi_lane.py private    default -> logoi,logos-raw   (nothing leaves the laptop)
python tools/logoi_lane.py fast       default -> nvidia,gpt-oss-20b (about 8x faster)
```

It rewrites `Router.default`, restarts ccr with the keys injected from the registry, then **reads
the config back and checks the service is up** before reporting success. Verified in both
directions, about 13 seconds each way.

**Three traps hit while writing it, all worth keeping:**

1. **`ccr start` is a SERVER and never returns.** A `subprocess.Popen` child that inherits stdout
   holds the pipe open, so the caller hangs forever. This is the same "runs in the foreground" trap
   already recorded, met again from a different direction.
2. **`DETACHED_PROCESS` does NOT work here.** It was the obvious fix and the service silently failed
   to come up, because PowerShell wants a console. What works is a **short-lived PowerShell whose
   only job is `Start-Process ... -WindowStyle Hidden`, which then exits.**
3. **`ccr status` output breaks a cp1252 decode.** It prints box-drawing and emoji, so
   `subprocess.run(..., text=True)` raises `UnicodeDecodeError` and a verification step wrongly
   reports failure on a change that actually succeeded. Always pass
   `encoding="utf-8", errors="replace"` when reading ccr.

## 🧮 LOCAL SPEED: MEASURED, AND THE FREE TUNING IS A REGRESSION (2026-08-23 evening)

**The laptop already runs at 86% of its physical memory-bandwidth ceiling.** That single number
explains everything below and should stop this being re-litigated.

```
single channel DDR4-2400 = 19.2 GB/s  ÷  5.2 GB model  =  3.69 theoretical
                                                 MEASURED  3.16   ->  86% efficiency
dual   channel DDR4-2400 = 38.4 GB/s  ÷  5.2 GB model  =  7.38 theoretical
                                          86% of that  =  6.3   <- what dual channel would give
```

Token generation requires reading essentially the WHOLE model out of RAM per token, so bandwidth is
the ceiling and the CPU mostly waits. At 86% there is no headroom left to tune. **The only lever is
more GB/s.**

### The tuning was tried properly and MADE IT SLOWER

| config | median tok/s |
|---|---|
| baseline, no flags | **3.16** |
| `OLLAMA_FLASH_ATTENTION=1` + `OLLAMA_KV_CACHE_TYPE=q8_0` | 2.71 (**-14%**) |
| the same plus `num_ctx` 40960 -> 8192 | 2.81 (-11%) |

All three levers target the KV cache, and on short prompts the KV cache is NOT the bottleneck.
Flash attention is a GPU optimisation; quantising the cache adds CPU work to save bandwidth that
was never the constraint. **Reverted.** Only `OLLAMA_KEEP_ALIVE=30m` kept, which avoids paying the
16s model load repeatedly. Measure with `tools/logoi_bench_ollama.py` (reads Ollama's own
`eval_count` / `eval_duration`, so tok/s is computed, never felt).

⚠️ **Variance is ±15% from thermal throttling on this 15W chip**, which is larger than most effects
being tested. Always take a median of 3 with a warm-up, on the same power state.

### 💥 OLLAMA ORPHANS ITS llama-server CHILDREN

Force-killing the `ollama` parent leaves `llama-server` children running with the model still
resident. Found **six orphans holding 7.2GB**, two of them dated 22 Aug, so this predates any one
session. Commit charge had reached 45.7GB of a 48GB limit and `qwen3:8b` could no longer load at
all: `failed to allocate buffer of size 3312451584`. Clearing them took free RAM 4.3GB -> 11.6GB.

**Check `Get-Process llama-server` whenever the model refuses to load.** Kill any whose StartTime
predates the current `ollama` process.

### 💰 THE HARDWARE ANSWER (prices checked live 2026-08-23)

- **RAM is NOT €30.** Cheapest 16GB DDR4 SO-DIMM on Geizhals at 18:27 was **€99**; DDR4-2400 parts
  specifically from €159.90. DDR4 is end-of-life and rising. So **€99 buys about 2x**.
- **A CPU VPS mostly LOSES.** Measured, scaled to this 5.2GB model: Hetzner CCX23 (4 dedicated
  vCPU) = 5.52 tok/s, SLOWER than the RAM stick, at €86/mo. CAX31 = 5.74, also slower. CAX21 = 3.20,
  identical to the laptop. Only CPX41 (12.16, €69/mo) and CCX43 (13.13, €276/mo) clearly beat it,
  costing more monthly than the stick costs once.
- **A used RTX 3060 12GB measures 51.6 tok/s on this exact workload**, 16x the laptop, because it
  has 360 GB/s against 19.2. About €200-250 once, in a box King owns, reached over Tailscale which
  is already installed. Note an L4 (the common cloud inference GPU) measures 42.9, i.e. SLOWER than
  a used 3060 costing less than two months of renting it.
- **So: €99 buys 2x, €250 buys 16x.** The GPU box is the better value and the only option that is
  both fast and private. **Nothing bought yet; King's call.**
- ⚠️ A VPS cannot do the job the local model exists for. The local lane is about PRIVACY (his brain,
  faith files, unsigned-IP Klarnow code). A rented VPS is still someone else's machine, so it
  replaces the free cloud lane, not the private one.
