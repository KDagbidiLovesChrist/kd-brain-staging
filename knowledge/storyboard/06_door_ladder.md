# 6 · The door ladder · which window to open, and who gives the orders

**Part 5 said what a harness is. This part says which one to open, in what order, and what happens
when one runs dry. It also names the one thing no ladder can do: tell you how much is left inside
most of the doors.**

```
DOOR     a window you open to work in     ccr code, Claude Code, Codex, ... Ollama
LADDER   the order you try them in        the everyday door first, the floor last
```

---

## 6.1 The ladder, as you ruled it on 8 September

| # | door | best for | what it spends | tonight, 20:17 |
|---|---|---|---|---|
| **1** | `ccr code` | everyday work, the default | **paid on 5 of 6 routes**; measured USD 0.00 (6.3) | open, service up |
| **2** | Claude Code | the chair: judgement, contracts, terminal work | your Claude plan, already paid | open, signed in as Kingdavidagb@icloud.com |
| **3** | Codex | web interfaces, hard architecture | your ChatGPT plan (Plus) | open, on a plan |
| **4** | Antigravity | visual work, image mockups, a free second opinion | Google's free allowance | open, kingagbidi@gmail.com |
| **5** | Copilot CLI | several vendors under one login | a plan, if you have one | open, plan unknown |
| **6** | Hermes | real, on Oracle, phone reach via Telegram | cheap, gemini-3.8-flash on OpenRouter | **open, on LOGIC-B** |
| **7** | Ollama | the floor: private, always there | nothing, ever | open, service up |

Also installed, not on the ladder: the Gemini CLI.

**When one runs dry, go down the list. When they all run dry you are still working, on rung 7.**
That is the whole point of having a floor that cannot run out.

---

## 6.2 Two rules that beat convenience

- **Faith work: rung 7 only.** Never a cloud door, whatever the queue looks like.
- **Contract and agreement work: rung 2 only.** One vendor, never local, never a third party.

If a lane rule and convenience disagree, the rule wins, and it is said out loud rather than
quietly swapped.

---

## 6.3 Where the ladder and the laptop disagree tonight

- ✅ **Door 1 is not free, and that is now written down rather than pending.** Five of its six routes
  go to OpenRouter's `gemini-3.8-flash`, paid per call; only `background` is free, on the local
  `llama3.2:1b`. **Ruled 12 September: option B**, keep the paid routes and correct the wording,
  because the measured spend on the current key is **USD 0.00**. It is the everyday door and it
  costs nothing in practice, but the ladder no longer calls it free.
- ✅ **Door 6 is no longer missing, and it did not turn out as planned.** Hermes is real now,
  installed on Oracle (LOGIC-B) on 13 September, reached from the phone through a Telegram bot
  (@BotFather-issued token, locked to your numeric user ID only). But it needs 64,000 tokens of
  context and your local models run at 4,096, so it cannot be the free local grinder the plan
  called for. It runs on OpenRouter's `gemini-3.8-flash`, the same cheap model ccr already uses,
  measured near-zero cost. **Door 6 is real, and it is a phone door, not a free one.**
- **The index promised doors 0 to 7.** Your ruling has seven doors, 1 to 7, and nothing in the brain
  defines a door 0. If you meant your own engine, it is not a door you open by hand; it is the
  governed machine the doors feed (part 9). Yours to rule.

---

## 6.4 The honest limit: what can be counted

**A script can read:** OpenRouter credit, Copilot usage when there is a plan, the health of your
local services (Ollama, LOGOI, the deck, ccr), and your engine's own spend ledger.

**A script cannot read:** the Claude plan bars, Antigravity's bars, the Gemini free tier, the
OpenAI balance that Codex spends.

So the ladder can say which door fits the job, and never how much room is left in it. Before a long
session on a paid door, glance at the bar inside the app. Anything that claims to know that number is
guessing.

Underneath it sit your two economies from 8 September:
- **subscriptions** (a flat monthly allowance that refreshes) carry the **interactive work in a
  harness**, and cannot surprise you with a bill;
- **keys billed per token** carry only the **automated work in your engine**, where the spend gate
  and the monthly envelope govern every call.

That is part 5's rule again from the other side: three surfaces, two governable, and ccr the only
bridge.

---

## 6.5 The chain of command, seen working today

Door 2 gave the orders, door 3 did the building, and cheaper horses carried the legwork.

```
KING  --rules-->  CLAUDE, door 2  --brief-->  CODEX, door 3  --spawns-->  helpers
                  the chair                   lead: Astra, medium         scout: Luna, low
                     ^                                                    builder: Terra
                     +------ checks red then green, then pushes ---------+
```

What happened, in order, on 11 September:
- **Afternoon:** Codex ran out of its Plus allowance mid-task. Every step had run on its dearest
  model, `gpt-6-astra`, at effort `high`, with no helpers. Claude finished that job.
- **17:11:** Astra lowered to `medium` as the lead, and three helpers set up: the scout and the bulk
  worker on `gpt-5.6-luna`, the builder on `gpt-5.6-terra`. On Plus, a 5-hour window allows 5 to 45
  Astra messages but 250 to 2,000 Luna ones.
- **19:41, the proof:** a read-only job. The lead ran on Astra at `medium`, the scout on Luna at
  `low`, the answer was correct, and it used 29,613 tokens in a minute.
- **19:51, the first real job through the chain:** the fabrication checker fix. From brief to engine
  commit `e19ea89` in about five minutes. Claude took the fix out and put it back to watch the new
  test fail and then pass, before pushing.
- **20:17:** the second, the money workspace, handed over while this part was written.

**The rule it makes:** the chair writes the order and checks the work; the builder builds; the
legwork goes to the cheapest horse that can carry it. Door 2 is dear to think with, so it does not
grind.

---

## REAL TODAY

| | |
|---|---|
| **real** | The seven-rung ladder, now with all seven doors real (door 6 landed 13 Sep, on Oracle rather than the laptop); `/doors` and `tools/harness_status.py` read them; the chain from Claude to Codex to its helpers, proven twice |
| **half built** | Door 1 is the default but paid on five of six routes; Copilot's plan is unknown; the allowance inside most doors cannot be read |
| **zero** | any door 0. Door 6, Hermes, moved to real on 13 September. |

⚠️ **The ladder tells you which door. Only the app tells you how much is left in it.**

**Proof:** read and run on 11 September:
- `python tools/harness_status.py` at 20:17: the door states above and ccr's six routes, 1 free and 5
  paid;
- `commands/doors.md` and `knowledge/HARNESS_MAP_2026-09-08.md`, for the ruling itself;
- Codex's session files in `~/.codex/sessions/2026/09/11/`: the lead `...T19-41-34...` on
  `gpt-6-astra` at `medium`, the scout `...T19-41-53...` on `gpt-5.6-luna` at `low`;
- engine commit `e19ea89`, and Claude's own red then green re-run of it;
- OpenAI's Codex pricing page (learn.chatgpt.com/docs/pricing), for the Plus numbers.

**Next:** [7 · The command centre](07_command_centre.md)
