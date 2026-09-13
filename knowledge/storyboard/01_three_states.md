# 1 · The three states: HW, SW, CW

**Everything you own is in one of three states. The same object can change state.**

That last sentence is the useful part. A hard drive on your desk and the same drive plugged in
are not the same thing, and the difference decides what it can do and what can go wrong with it.

---

## 1.1 HW · hardware

**Powered, connected, in the flow, able to act right now.**

| what | what it is | state today |
|---|---|---|
| the laptop | your main machine. Runs the models, the engine, the boards. | 19.88 GB RAM, and it is the bottleneck |
| **Oracle** | a rented Linux box. 2 ARM cores, 10.9 GB. Never sleeps. | up, all services active |
| the phone | a window onto both, over Tailscale | works |
| the drive, **when plugged in** | see CW below. Plugging it in changes its state. | usually unplugged |

**Oracle is rented, and the rent is not money.** It is a free-tier box, and free-tier boxes get
reclaimed when idle. The keep-warm job is what stops that. **The standby duty is the rent.**

---

## 1.2 SW · software

**The instructions. The sequences. What tells the hardware what to do.**

```
the engine        :3000, and its deck on :3200
the tools         the Python and PowerShell in tools/
the hooks         5 of them, firing inside a Claude Code session
the scheduled jobs 25 of them, firing on a clock
the skills        the /commands. INSTRUCTIONS, not reasoning. See part 3.
```

**Software alone does nothing.** A tool nobody runs is a text file. That sounds obvious and it is
the reason part 3's equation works.

---

## 1.3 CW · coldware

**Real, complete, and inert. GitHub and the hard drive.**

Both hold everything. Neither reasons about anything. Neither acts.

| | GitHub | the drive |
|---|---|---|
| what it holds | **5,003 tracked files** | brain, engine, models, OneDrive, Google Drive, the vault |
| git history | full | full, as a real clone under `brain/kd-brain` |
| the encrypted vault | **never, correctly** | **yes**, 5.32 MB, AES-256 |
| the 8.3 GB of models | no | **yes** |
| kept in step by | the 15-minute sync | a nightly mirror at 03:30 |

**They are two cold stores holding overlapping but different things.** GitHub has no keys. The
drive has the keys but is a copy, not a live tree. **Neither one alone is a complete restore.**

### Why "coldware" is a real category and not a filing label

A cold store is not broken and it is not merely backup. **It is a complete component with one
input missing on purpose.** The drive holds more knowledge than Oracle does and 8.3 GB of models,
and it does nothing at all, because there is no machine attached.

That is exactly why it is safe. **A thing that cannot run also cannot leak, cannot be reached
over a network, and cannot be stolen while it sits in a drawer.**

### One caution about the word

"Cloudware" and "coldware" are your words and they work inside this estate. **A buyer hears
something else.** In the industry, cloudware means software delivered from someone else's cloud,
which is close to the opposite of what you have built. Say it precisely in a client room or use a
different word there.

---

## 1.4 The models, which are CW until loaded and HW once running

```
logos-qwen3:8b            5.2 GB    your own baked model. the free floor.
qwen3:8b                  5.2 GB
llama3.2:latest           2.0 GB
llama3.2:1b              1.3 GB    the cheap lane
nomic-embed-text          274 MB    embeddings for retrieval
                         ───────
                          8.3 GB    on disk, and on the drive
```

**`logos-qwen3:8b` needs roughly 6 GB of RAM to run.** On a 19.88 GB machine that is fine until
editors, extensions and browsers take their share. When they do, the free floor cannot load, and
**everything falls to paid at exactly the busiest moment.** Part 7 has the measurements.

---

## REAL TODAY

| | |
|---|---|
| **real** | all three states, with everything above counted live tonight |
| **half built** | the drive and GitHub are in step *now*, after a repair. See below. |
| **zero** | nothing here is aspirational |

**Proof:** `git ls-files` → 5,003. `ollama list` → the five models. Drive contents read directly
from `D:\KD-LOGOS`.

**One thing you should know about that "in step".** The nightly mirror had been pulling from the
brain's **old** location since it moved on 9 September. It succeeded every night against a folder
that had stopped changing, so nothing looked wrong while the drive fell **198 commits behind**,
with the vault sitting on it. Repaired 10 September; the remote is now checked on every run, and
a test pins it.

**Next:** [2 · Cloudware](02_cloudware.md)
