---
name: lllm-logic-layer-2026-08-25
description: The LLLM architecture King specified, what got built (the gate fix and the governor), and the measured numbers behind every decision
metadata:
  type: project
---

**2026-08-25, a long overnight session.** King specified the whole LLLM system out loud, and two
pieces of it were built, proven and put live. Everything below was measured on his machine, not
estimated.

## His framing, and it is the important line

> **"THE WAT PROMPT IS WHAT BUILT THIS ARCHITECTURE. WE ARE NOW ADDING THE LOGIC, THE
> INTELLIGENCE LAYER."**

W, A and T built the structure. **L, Logic, is what is being added now.** So this work is the
last letter of his own framework, not a new project beside it. He also refined the acronym:
**LLLM is Layman Local Large LOGIC Model**, not Language.

## The numbering he settled on

    000   the 3D world, the face, plus the Logos engine as back end
     00   Ollama, local, free, the GOVERNOR
      0   Claude, escalated to only for genuinely hard work
    1-9   the Logoi agents, the workers

## WHAT WAS BUILT AND IS LIVE

**1. The gate now reads the whole letter, not the envelope.** `logoi_gate.check()` inspected only
the question, but `logoi_envoy.ask` transmits `[system_prompt, question]` and BOTH retrieval
routes put his notes in the SYSTEM message. **`retrieval_sources` was never once passed by the
only caller that exists, so the rule "retrieved notes never travel" had never fired in
production.** His notes were safe only because that one route happened to do no retrieval, which
is a property of one call site and not a guard.

Fixed: the gate now inspects everything transmitted, refuses any system prompt not explicitly
registered (fails closed, because notes get appended to the system prompt so an unrecognised one
IS the evidence), and the 22 faith words moved from `ollama_gui.py` into the gate so they cover
**every** lane. The remote lane, the only one that leaves the machine, previously had no faith
check at all.

**⚠️ THE TEST CAUGHT A BUG IN THE FIX, AND A WORSE PRE-EXISTING ONE.** Naive substring matching
refused **14 of 16 ordinary business phrases**: `"the meeting agenda"` blocked by **nda**,
`"python versus java"` by **rsu**, `"excellent work"` by **lent**, `"breakfast meeting"` by
**fast**, `"reverses a list"` by **verse**, `"my grandfather"` by **father**. The agenda and
versus cases were live before this session. Now whole-word matched. **A guard that refuses
ordinary work gets worked around, and then it protects nothing.**

Prover: `tools/prove_gate_reads_the_whole_letter.py`, **36 checks, 0 failed**, and verified
against the running service, not only in tests.

**2. LOGOS the governor, `tools/logos_policy.py`, built and wired into `ollama_gui.py`.**

    14 requests routed in 3.4 ms      0.24 ms each
    a model doing the same job        7,000 to 9,000 ms each

**Measured, which is why the governor is code and not a model:** plain "EASY or HARD" on
`llama3.2:1b` took 1.0 s; a full routing decision took 7 to 9 s; the same on the 3B took 18.6 s
for the same answer; and removing the reason field made it 4 to 7 s **and wrong**. So the model
needs to reason to route correctly, and that reasoning costs 7 to 9 seconds on every message.

**King's own quality rule was PRESERVED, not reversed.** `pick_model` sent note-backed questions
to the 8B, and his comment gives the reason: *"it never silently downgrades a question that
reached for his notes, because that is where answer quality actually matters."* The audit called
that backwards for speed. Both are defensible, so `NOTES_MODEL` is a one-line switch defaulting
to his choice. What genuinely was wrong is the FAITH lane inheriting the deep model, since faith
always retrieves and the scripture tool does the actual finding.

## THE NUMBERS THAT SHOULD SURVIVE THIS SESSION

**Cost per mission, from his own meter** (591 gateway responses over 21 missions, ~28 model calls
per mission, ~501 input and ~81 output tokens per call):

    local ollama   EUR 0.00        Haiku 4.5   $0.025
    Sonnet 5       $0.051          Opus 4.8    $0.127        Fable 5   $0.254

So 500 missions a month on the strongest model costs about **$63**. The margin argument: routing
everything to the strongest model costs $0.127 a mission; letting the governor send routine work
to local and cheap lanes costs about **$0.018**, seven times less, same client experience.

**The faith lane is hardware-bound, not routing-bound.** Warm, correctly routed to the 3B, it
still takes **49 to 65 seconds**: it reads ~975 tokens and writes ~300 at about 5 tokens a second
on a CPU with no GPU. **A used RTX 3060 12GB, about EUR 250, measures 51.6 tok/s, sixteen times
this laptop.** That turns a 50 second answer into about 3 seconds and is the highest leverage
spend in the whole plan.

## STILL OPEN, and the first one matters most

- **The ceiling that stops money is NOT built.** `LOGOS_CLIENT_BUDGETS` is read in exactly one
  place, the `/api/usage` reporting route. **Setting a budget changes a number on a page and
  stops zero calls.** Worst case today is genuinely EUR 0 because there is no Anthropic key and
  `LOGOS_LOCAL=1`, but the moment a paid tier ships there is no ceiling.
- **The grounding gate fails to COMPLETE 57% of the time**: 276 `check_failed` against 122
  passed and 85 failed. It fails closed, which is right, but that is not a shippable commercial
  control for an autopilot product. Cause is malformed JSON, and the judge is the same
  `qwen3:8b` that wrote the answer because `LOGOS_GROUNDING_MODEL` is unset.
- **No web search exists in LOGOI at all.** Zero hits for `search_web`, `firecrawl`, `perplexity`,
  `brave`, `tavily`. One of his three named sources is simply not built.
- **No self-serve signup.** Tenants are created by hand-editing `prisma/seed.ts` and restarting.
- **ccr's default route is NVIDIA with no gate**, so anything run through `ccr code` sends every
  file it reads to NVIDIA with no audit row. This session was NOT routed through it (no
  `ANTHROPIC_BASE_URL` set), but that path is open.
- **Agents are still printed inside the engine** as TypeScript in `src/lib/workers/`. Until they
  are records, the fan out cannot dispatch them, they cannot be adapted per client, and the
  engine cannot be open sourced. **This is the engine being restructured, not his 923 brain
  files.**

## CORRECTIONS TO THE RECORD

- **"923 files" is wrong.** Measured: **540 allowed, 391 blocked, 931 matched**, and the
  retrieval globs are only two folders deep so anything deeper is invisible. Total markdown in
  the brain is **3,746**.
- **Parallel fan out already exists**, in `sovereign.ts:137`, running concurrent calls and
  refusing to substitute a failed run. What is missing is fan out across DIFFERENT models.
- **The brain wire has been used exactly once** in 1,868 audit rows, and that one run pulled two
  guarded files, which is what forced the guard fix.

## LATER THE SAME SESSION: the ccr router, and the road that had no gate on it

**THE LEAK, now closed.** `ccr`'s `Router.default` was `nvidia,openai/gpt-oss-20b` and
`CUSTOM_ROUTER_PATH` was **empty**, so everything run through `ccr code` sent every file it read
to NVIDIA: no gate, no guarded-subject check, no path check, no audit row, including
`the-truth/`, `_private/` and `legal/`. Meanwhile `logoi_envoy.py` deliberately ranks NVIDIA
LAST behind seven OpenRouter models because its data policy is unresolved. Both could not be
right. Separately the config declared a `logoi` provider that **no Router entry pointed at**, so
his own local model carried exactly zero traffic while being described as wired in.

**Built:** `.claude-code-router\custom-router.js`, wired via `CUSTOM_ROUTER_PATH`, ccr restarted.
Config backed up to `config.json.bak-2026-08-25`. **`prove-router.js`: 18 checks, 0 failed.**

**It reads the guarded lists out of `logoi_gate.py` rather than keeping a JavaScript copy**, per
King's own rule that two copies of a safety list drift and the copy that drifts is the one
holding the rule. Add a guarded subject to the Python and it applies to the router on the next
request with nothing to remember.

**WARNING, THE TEST CAUGHT ME CLAIMING SOMETHING UNTESTED.** The first "fail closed" checks
passed, but they passed via the *trivial* branch, so the failure path they claimed to prove had
never run. Same class as `prove-sovereign` passing for months with zero assertions. `GATE_FILE`
is now overridable by `LOGOS_GATE_FILE` purely so the failure branch can be exercised, and the
real test points it at a missing file and confirms ordinary work is held LOCAL rather than
sailing through.

**A verified fact about this session:** it was NOT routed through ccr. No `ANTHROPIC_BASE_URL` is
set, so nothing read tonight went to NVIDIA.

**Also confirmed as already existing**, against what King thought still needed building: `ccr`
already routes Claude through OpenRouter and NVIDIA (that IS the "github code"); Claude directing
and deploying versions of itself is subagents, proven tonight at 9 agents and 1.1M tokens with
zero errors; and plan, bypass and manual modes are already built into Claude Code
(`defaultMode: auto`, 30 allow rules, 7 deny). **The consumer versions already exist too:** the
Clarity Brief is plan mode, the approval gate is manual, and autopilot with a typed RED override
is bypass.

## Cross references

[[project-logos-jarvis-mode]] (his rulings and the faith lane decisions) ·
[[project-logos-os-whole-picture-2026-08-24]] (the long term picture) ·
[[project-logos-engine-fixes-2026-08-25]] (the engine work secured earlier the same night) ·
[[feedback-no-legal-advice-king-ruled]]
