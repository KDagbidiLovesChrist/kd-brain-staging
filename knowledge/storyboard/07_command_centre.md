# 7 · The command centre · the seat, and what it may spend

**Part 6 said which door to open. This part says where you SIT, what every button on that seat
actually reaches, and the question that follows immediately: who is counting the tokens.**

```
DOOR         a window you open to work in       ccr code, Claude Code, Codex ... Ollama
THE SEAT     where you run the ESTATE from      KD Vault, 127.0.0.1:5056
```

A door is somebody else's window with your work in it. The seat is yours.

---

## 7.1 The seat, measured

The KD Vault on `127.0.0.1:5056`. Built and live, and it already carries more than any part of
this document had described.

| on the seat | what it is | reaches |
|---|---|---|
| **Talk to your aide** | the front door, tap the orb or type | LOGOI, local only |
| **What is going on** | the ecosystem measured live, every port | `/dashboard` |
| **Brain** and **Ecosystem** | memories, index size, uncommitted count | `/?sec=brain`, `/?sec=eco` |
| **Eden village** | the five halls as realms, live machine counts | `127.0.0.1:5055` |
| **Eden World (3D)** | the 3D world | a published artifact |
| **Brain Village** | the simulation | `/sim` |
| **Topology graph** | the brain drawn as a graph | `/brain/BRAIN_GRAPH.html` |
| **DCIM** | the data centre view | `/brain/BRAIN_DCIM.html` |
| **n8n workflows** | the automation floor | `127.0.0.1:5678` |
| **Obsidian** | the notes, opened natively | `obsidian://open?path=...kdbrain` (repointed 12 Sep, see 7.5) |
| **Notion mirror** | the outside copy | notion.so |
| **Command deck** | 64 Logic commands, tap to copy | paste into any door |

**System vitals on the seat tonight:** 64 Logic commands, 57 plugin skills, 0 waiting to be
filed.

---

## 7.2 The four surfaces, and why they are not one thing

King asked it exactly right on 12 September: *"is it all thru ccr for token management?"*

**No, and that is not a gap to close. They are different jobs.**

```
1. THE SEAT        your GUI. Your work. Governed by your engine.
2. THE DOORS       somebody else's window. Claude Code, Codex, Antigravity, Copilot.
3. THE BRIDGE      ccr. A guard placed in front of ONE of those windows.
4. THE FLOOR       Ollama. Free, local, always there.
```

**A door talks straight to its vendor.** His own words, 8 September. `ANTHROPIC_BASE_URL` is
unset, so a plain `claude` never touches ccr at all. Codex talks straight to OpenAI. Nothing of
his sits in between to count or refuse.

**ccr is a bridge, not a meter.** Its job is to put his guard in front of a harness window. That
is why it exists, and it is why it is the only harness he can govern.

**The engine is the meter.** The spend gate, the travel gate, the lanes table, the audit log and
the ledger all live there. So the seat talks to the **engine**, never to ccr. The seat is his own
work; ccr is for somebody else's window.

One detail worth knowing, because it points the other way: **ccr's config already has a provider
called `logoi`, pointing at `127.0.0.1:5056`.** The bridge can already route a harness window
back into his own brain.

---

## 7.3 Token management, said exactly

This is his own rule from 8 September, and it is the answer to his question.

| | economy | carries | can it be metered |
|---|---|---|---|
| **subscriptions** | flat monthly, refreshes | the interactive work, him at the keyboard | **no.** Read the bar inside the app. |
| **keys billed per token** | per call | the automated engine work | **yes.** Spend gate, envelope, ledger, receipt per call. |

**So token management is not one dashboard, and a design that promises one is lying.** It is a
real meter for the engine, and a bar you read by eye for the doors.

**What a script can read:** OpenRouter credit, Copilot usage when there is a plan, the health of
the local services, and the engine's own spend ledger.

**What a script cannot read:** the Claude plan bars, Antigravity's bars, the Gemini free tier, the
OpenAI balance Codex spends.

That is part 6's honest limit, arriving again from the other side: **the seat can say which door
fits the job, and never how much room is left in it.**

---

## 7.4 What the seat governs, when it governs

The chain, when work goes through the engine rather than through a door:

```
THE SEAT --> THE GOVERNOR --> THE GATE --> a model --> THE LEDGER
   :5056       0.24 ms          reads the       local or       a receipt,
               picks lane,      question AND    remote         every call
               model, budget    the notes
```

- **The governor** decides the lane, the model and the reply budget in 0.24 ms. A model asked to
  do the same job took 7 to 9 seconds, which is why the policy is code and not a model sitting in
  the request path.
- **The gate** decides whether it may leave, and it reads the question **and** the retrieved notes
  as one body, because notes are appended to the system message and reading only the question was
  the 26 August bug.
- **The ledger** takes a receipt for every call that spent anything.

**King's ruling, 12 September.** A clean notes question may now take the remote lane, which is
several times faster. Guarded subjects, faith, guarded paths and long pastes still stay home, and
so does anything guarded that retrieval drags into the prompt behind a clean question.

**Switched on and proven live the same evening**, 12 September 21:33, both directions: a clean
notes question answered in **3.6 seconds** against 21.1 locally, and a cap-table question was
refused the fast lane and answered at home in 277.4 seconds.

⚠️ **Building it found the remote lane had been dead for three days.** On 9 September King's
Maths was appended to `BIG_LANE_PROMPT`, and that text carries his full name and the word
*theosis*, which is on his own guarded list. So the gate refused EVERY question on that lane,
including "what is the capital of France". Had the gate not caught it, the lane would have
handed a vendor his name and his Theosis material on every call. The outgoing identity is now
frozen before that append.

---

## 7.5 Where the seat and the laptop disagree tonight

✅ **FIXED 12 September, the same evening it was found.** The Obsidian button had pointed at
`C:\Users\Dell\.claude`, the rollback copy, whose last commit was **9 September**, while the
live brain's was **today**. For three days that door opened a stale copy, and anything written
through it landed where the sync does not watch. It now points at `kdbrain`.

**This is the same failure as the drive mirror**, which succeeded every night against a folder
that had stopped changing while the drive fell 198 commits behind. A path that still resolves is
not a path that is still right.

⚠️ **The n8n button opens an empty floor.** Nine workflows, **none active**, read from n8n's own
database. Two of the nine are not workflows at all, they are wall charts of sticky notes. Mean-
while `KD_n8n_KeepAlive` faithfully keeps the server up so that nine switched-off workflows stay
reachable.

⚠️ **The partner engine on :3100 is down.** Seven of eight services answered tonight.

---

## REAL TODAY

| | |
|---|---|
| **real** | the seat, live on :5056, with all twelve doors on it and the command deck; the governor, the gate and the ledger behind it; 7 of 8 services answering |
| **half built** | token management: the engine half is metered, the door half can only be read by eye, and no single screen says so yet |
| **zero** | any dashboard that claims to know what is left in a subscription. It cannot be read, and part 6 says so |

⚠️ **One stale door left on a live seat:** n8n opens a floor with nothing switched on. The
Obsidian door was repointed the same evening.

**Proof:** button targets read directly from `_ops/VAULT_HUD.html` lines 147 to 159. Ports listened
on at 18:4x on 12 September, seven of eight answering. n8n's nine workflows and their zero active
count read read-only from `~/.n8n/database.sqlite`, `workflow_entity`. ccr's five routes and its
five providers read from `~/.claude-code-router/config.json`. Both brain paths checked with
`git log -1`: `.claude` at 9 September, `kdbrain` at today. Frame 5 proven live at 21:33, both
directions, restart verified by PID.

**Next:** [8 · WAT and the recipes](08_wat_and_recipes.md)
