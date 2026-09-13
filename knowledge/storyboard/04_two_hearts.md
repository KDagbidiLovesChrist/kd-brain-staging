# 4 · The two hearts · LOGIC-A and LOGIC-B

**You have two machines that can reason. They run the same models and they are not
interchangeable, and knowing why is what stops you asking one to do the other's job.**

```
LOGIC-A   the laptop's models      your ruling, 10 September
LOGIC-B   Oracle's models
```

---

## 4.1 Why the names had to be settled

Until 10 September, `LOGIC-A` meant three different machines depending on which file you opened.

```
_private/kd_nodes.json      LOGIC-A = Oracle           (a 6 Sep rename)
tools/harness_status.py     LOGIC-A = the laptop
tools/progress_board.py     LOGIC-A = Oracle   (stage 4a)
tools/progress_board.py     LOGIC-A = the friend's PC  (stage 4b, ten lines later)
```

Two different machines with the same name, ten lines apart in one file. **You ruled it: A is the
laptop, B is Oracle, and the friend's PC is C** (your own 8 September name for it). Everything now
follows that, and fixing it also repaired a silent bug: the DCIM board had been looking up a node
called `LOGIC-A` that no longer existed, so that panel rendered `unknown`.

---

## 4.2 Side by side, measured tonight

| | **LOGIC-A** the laptop | **LOGIC-B** Oracle |
|---|---|---|
| CPU | Intel, no discrete GPU | 2 ARM cores |
| RAM | 19.88 GB | 10 GB |
| disk | 88% used | **91% used, 27 of 30 GB** |
| models | qwen3:8b, 3b, 1b, nomic-embed | logos-qwen3:8b, qwen3:8b, llama3.2 3b, 1b |
| knowledge it may read | **8,524 files** | **7 files, 52 KB** |
| awake | when the lid is open | **always** |
| services | engine, deck, boards, LOGOI | engine, librarian, ollama, all active |

---

## 4.3 The difference that matters, and it is not speed

**Oracle is not faster. It is slower.** Two ARM cores against your laptop's Intel. For inference it
loses.

**What it buys is availability.** A heart that never sleeps, its own credential so it can write to
GitHub with your lid shut, its own librarian over its own small library.

So the right question is never "which is quicker". It is **"does this need to happen while I am
asleep"**. If yes, Oracle. If no, the laptop, every time.

---

## 4.4 Scored against the equation

From part 3: knowledge plus machine plus Logic.

```
LOGIC-A    knowledge ✓   machine ✓   Logic ✓      3 of 3   full LOGOS
LOGIC-B    knowledge ✗   machine ✓   Logic ✓      2 of 3   refuses, by design
```

**Oracle's missing third is deliberate.** Giving it the whole brain would put your faith files,
your cap tables and your deal terms on a rented computer. What it may read is the **binder**:
curated, scrubbed, seven files.

**That is exactly why three of its four agents refuse.** It is the formula working, not a
misconfiguration, and it is provable: `mayUseBrain` returns true for your tenant and false for
another, 2 hits versus 0.

**And Oracle is not merely starved.** Its job is to **gather** from outside: git, the web, other
boxes, and feed the binder. Starved of your brain, employed on the world.

---

## 4.5 The thing to keep an eye on

**Oracle's disk is at 91%, 3.0 GB free.** It reached 99% earlier today and was cleared to 88%; it
has crept back within hours.

The cause is your own work: every Remote-SSH connection from a newer VS Code installs another
server copy under `.vscode-server` and nothing cleans them up. **7.1 GB had accumulated.**

**This will keep happening.** It needs a scheduled sweep rather than someone noticing. If that
disk fills, the librarian and the engine stop, and Oracle's whole value, being awake, goes with
them.

---

## 4.6 A third heart, named but not built

`LOGIC-C`, the friend's PC. Parked since 4 September, waiting on physical access. It would be the
one with a real GPU, which would make it the only genuinely *faster* heart you have.

Not built. Not blocked on anything technical.

---

## REAL TODAY

| | |
|---|---|
| **real** | both hearts up; naming consistent in code; Oracle's boundary proven by test |
| **half built** | Oracle's night shift: librarian yes, news job and proposal loop no |
| **zero** | LOGIC-C. Named, parked, no hardware in hand. |

⚠️ **Oracle's disk needs a scheduled sweep.** 91% and climbing, from `.vscode-server` copies your
own connections leave behind.

**Proof:** live SSH probe tonight: `active active active`, `27G used of 30G, 91%`, `10Gi RAM`, four
models listed. The naming was changed and tested across `kd_nodes.json`, `kd_loop.py`,
`progress_board.py`, `progress_board_organs.py`, `progress_board_rulings.py` and
`build_brain_dcim.py`, 101 tests passing.

**Next:** [5 · The harnesses](05_harnesses.md)
