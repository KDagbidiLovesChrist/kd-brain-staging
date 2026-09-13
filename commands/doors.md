# /doors · which door to open, and what it will cost

**Trigger:** King types `/doors`, or asks "which AI should I use", "which one is cheapest",
"what have I got left", "where should I do this".

**What this is.** The Logic layer over the harness ladder. It answers one question: for the job in
front of him, which door should he open, and what does opening it cost. It never opens a door and
never spends anything. His hand does that.

---

## The two layers, because they get confused constantly

A **model** is the thing that thinks. A **harness** is the thing with hands: an editor, a terminal,
git. They run out differently, so they are rescued differently:

- **A model runs out** (a limit, a refusal, an empty answer). Fixed INSIDE the engine by the router
  walking down its lane, automatically. He never sees it.
- **A harness runs out** (a usage window closes, credit ends, the app dies). No router can fix that,
  because a harness window talks straight to its vendor. Fixed by: push, open the next door, pull,
  carry on.

That second half is what this skill is for.

---

## The ladder, in order

Ruled 2026-09-08. Rung 7 cannot run out, which is the whole point of having it.

| # | Door | Best for | What it spends |
|---|---|---|---|
| 1 | `ccr code` | everyday work, the default | **5 of its 6 routes are PAID** (OpenRouter, `google/gemini-3.8-flash`); only `background` is free, on the local `llama3.2:1b`. Corrected 11 Sep 2026: this row used to say "the free and near free lanes", which the routes do not support. |
| 2 | Claude Code | the chair: judgement, contracts, terminal work | a plan already paid for |
| 3 | Codex | web interfaces, hard architecture | a plan if signed in, otherwise metered |
| 4 | Antigravity | visual work, image mockups, a second opinion | free vendor allowance |
| 5 | Copilot CLI | several vendors under one login | a plan if he has one |
| 6 | Hermes | real, installed on Oracle (LOGIC-B) 13 Sep, reached from the phone via Telegram | cheap, gemini-3.8-flash on OpenRouter (not free; local models can't hold Hermes' 64k context) |
| 7 | Ollama | the floor. Private, always there | nothing, ever |

**When one runs dry, go down the list.** When they all run dry he is still working, on rung 7.

---

## Two rules that are not preferences

- **Faith work: rung 7 only.** Never a cloud door, whatever the queue looks like. Nothing of that
  kind leaves the machine.
- **Contract and agreement work: one vendor only** (rung 2), never local, never a third party.

If a lane rule and convenience disagree, the rule wins. Say so out loud rather than substituting.

---

## How to run it

```
python tools/harness_status.py                 the board
python tools/harness_status.py --lane faith    the board plus a recommendation
python tools/harness_status.py --json          machine readable
```

Lanes it knows: `faith`, `legal`, `private`, `code`, `webui`, `video`, `bulk`.

---

## The honest half: what cannot be measured

A script can read: which doors are installed, whether the local services are up, whether the cloud
node answers, the credit on the one provider that exposes it, and this machine's own recorded spend.

A script **cannot** read the remaining allowance inside most vendor apps. For those, this skill can
say which door fits the job and never how much room is left in it. So before a long session on a
paid door, glance at the bar inside the app. Anything that claims to know that number is guessing.

---

## The two economies, which is the money principle underneath all of it

- **Subscriptions** (flat monthly, allowance refreshes) suit **interactive work in a harness**. They
  cannot surprise him with a bill.
- **Keys billed per token** (no ceiling) suit **automated work in the engine**, where the router,
  the gate and the monthly envelope govern every call.

Putting interactive work on a metered key is the mistake this ladder exists to prevent.

---

## Where this runs

Both nodes. On the laptop it sees every door. On the cloud node it sees only what is installed
there and says so plainly rather than pretending. Same tool, same output shape, no second copy of
the rules to drift out of step.

Related: `knowledge/HARNESS_MAP_2026-09-08.md` (what is installed, and the faults found in it).
