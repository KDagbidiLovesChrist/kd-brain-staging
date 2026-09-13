---
name: mission
description: Fire a real brief into the Logos engine as a recorded, grounded, metered mission. Returns a mission id. Use when work should leave a trail rather than dying with the chat session. Not to be confused with /engine, which is the pay-grade quality yardstick.
---

# /mission · put the work through the engine

> **Not `/engine`.** That one is the pay-grade yardstick (`_ops/THE_ENGINE.md`), a standard for
> grading work. This one is the Logos engine, the machine that actually runs and records a
> mission. Two different things that unfortunately share a word. Built 2026-08-26.

## Why this exists

Until today the link ran one way. The engine could read King's brain. **His brain could not fire
a mission.** Checked, not assumed: every file in `commands/` and `tools/` was searched for the
engine's ports and returned ZERO callers. So work done in a chat window left no mission id, no
audit row, no grounding check and no meter line, while the engine sat there able to provide all
four.

That is the difference between an assistant and an engine, and it was one HTTP call away.

## What happens when you fire one

    mission.created     king                 an id, and your name on it
    station.started     king
    brain.consulted     diagnose_worker      it reads YOUR notes, not its recollection
    gateway.call        diagnose_worker      the model is asked
    ...
    grounding check                          every claim traced to YOUR OWN WORDS
    approval waiting                         nothing publishes without you

## How to run it

    python tools/logos_engine.py                      is the engine up, what can I see

    python -c "import sys; sys.path.insert(0,'tools'); import logos_engine as E; \
      print(E.fire('your brief here'))"

Returns in about 140 ms with a mission id. The work continues server side whether or not you
stay watching, so closing the terminal does not kill it.

Watch it: `http://127.0.0.1:3200` (the deck), or `E.progress()`.

## The rules that apply, and they are not optional

- **The brief is everything.** Measured on this machine: a full detailed brief PASSED grounding.
  A thin one invented *"people who buy hooks for faceless characters in games"* and *"boosting
  conversion rates by 40%"*. **The engine is exactly as grounded as the brief it is given.**
  Write it like you would write it for a person who knows nothing.
- **Async by default.** Diagnose takes 30 to 90 seconds on the local model. `wait=True` uses the
  inline path, which is what the partner's own code depends on, so do not make it the default.
- **His own instance only.** `:3000`. Port `:3100` is the partner's and is never targeted here.
- **Nothing publishes without a human.** The approval gate stands. A red tier needs a typed
  reason recorded in your name.

## Where it stops

The connector fires briefs into King's own tenancy. It does **not** approve, reject, or publish.
Those stay deliberate acts done by him, on the deck, where he can see what he is agreeing to.

Related: `tools/logos_engine.py` · `_ops/THE_ENGINE.md` (the other engine) ·
`memory/project_lllm_logic_layer_2026-08-25.md`
