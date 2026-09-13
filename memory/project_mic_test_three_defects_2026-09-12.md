---
name: project-mic-test-three-defects-2026-09-12
description: "King's own 12 Sep mic test found four real defects, all fixed test first and committed (engine 0b54a23 and 83ae7a0): Diagnose invented his Hook Engine from his own notes, the answer card spoke twelve minutes late then three times, the fact checker returned five wrong violations, and it held the verdict for 213.8 s. Also records four Claude errors of assertion-before-verification, and five named unfixed items."
metadata:
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-12T14:03:45.933Z
---

# The mic test that found four real defects (12 Sep 2026)

King ran Stage 6.5 himself, spoke two briefs, and every defect below came out of his own ears and
eyes rather than a test. Three subagents were dispatched on his ruling **"use multi agents to deal
with all three"**; Claude verified every result by hand before committing.

## What his own ears proved, and it closed this morning's defect
- Brief one, spoken: heard. Voice lane 1,583 ms.
- Brief two, spoken: heard. Voice lane 2,331 ms. His words: **"I heard KD say the card"**.
- The engine refused brief two correctly, quoting his own sentence back.

## DEFECT 1: Diagnose invented his own product into his aunty's brief
Offer produced: **"Sign up for The Buka's Hook Engine to get discovered by nearby diners"**, then
verdict `build`. The Hook Engine is his own 19 euro product, named nowhere in the brief.

**Cause, proven not guessed: retrieval.** `retrieve()` uses the brief itself as the query, and his
brief is quoted verbatim in `_ops/START_HERE_WINDOW.md` (Claude's own mic test script) eight lines
above a DIFFERENT founder brief. Two founder voices arrived in one prompt and only one was his.
The decisive evidence is the run that behaved: at 07:27 his words transcribed as "The booker is an
engine version in Dublin", which never matched that file, so the poisoned page was never retrieved
and that run stayed honest. Clean transcription poisoned, broken transcription clean, which is
backwards for every theory except retrieval. The 12 Sep Codex brief was REFUTED as the cause by
its own mtime (10:04, after the 07:29 run).

**Fix:** his words fenced as the only source of facts, plus a guard that catches a named phrase
present in the answer and in the notes but not the brief, logs `diagnose.notes_leak`, and re-asks
the brief alone. His notes still reach the model. 8 of 8.

## DEFECT 2: the answer spoke twelve minutes late, then three times
No new engine work after `station.finished` at 12:43:14, yet he heard it at about 12:55, 13:05 and
13:15. **Repetition cause, proven:** the "already spoken" key was a `useRef`, which does not
survive a remount, and a single 401 from `/api/world` remounts the subtree. **Delay cause,
measured:** Kokoro `generate()` 43,718 ms for one sentence, whole job 55,270 ms against a 45,000 ms
watchdog; under load the bundle import alone stalled 305,008 ms. The watchdog fired correctly
(45,011 ms) but can only release the queue, not cancel an utterance already accepted.

**King ruled option 4:** the answer speaks through the instant browser voice; Kokoro only if
already loaded and inside 2,000 ms. 55,728 ms became 19 ms. The late-clip trap is closed
structurally: the `Audio` element is constructed only inside the winning branch.

**Still unproven:** the hidden tab theory. Playwright launches Chrome with backgrounding disabled,
so it could not be reproduced. A trace line now records tab visibility for the next occurrence.

## DEFECT 3: the fact checker returned five wrong violations
Two triage faults, neither the model's: the engine renders `ANGLE: / AUDIENCE: / OFFER:` and
`namedThingsNotInBrief` read those labels as product names; and `specificsKeepNeighbours` demanded
every number keep a neighbour word from the brief, which a bare price can never do. Proof it was
triage: identical text appeared as a NOTE without its label and a VIOLATION with it. A third fault
found by a real Gemini call: "no" in "...no distribution, Launch A..." sat in the negation window
across a comma. 87 of 87.

## DEFECT 4: the audit held his verdict for 213.8 seconds
Now pre-filtered (4 of his 9 real verdicts skip entirely) and off the critical path (returns in
14 ms). Build is untouched at `builder.ts:310` because that one is a refusal gate.
**Cloud lane built, OFF by default** (`LOGOS_GROUND_CLOUD`): one real Gemini call 3,106 ms and
USD 0.000724 against 213.8 s locally. His tenant only, four client tenants refused with zero
requests reaching Google.

## FOUR CLAUDE ERRORS, all the same shape: asserted before verifying
1. Read a truncated offer string and told him "no Hook Engine". The full row said the opposite.
2. Warmed `llama3.2:latest` without checking what the tracer used, drove free RAM from 2.3 GB to
   0.1 GB, then said the warming was wasted. The audit row later showed `llama3.2` after all.
3. Reported a euro sign encoding fault in the engine. The DB held correct UTF-8; the mangling was
   Claude's own Python reader printing to a cp1252 console.
4. Raised a sync incident from a stale file snapshot, claiming his auto-sync had reverted a file.
   The file was intact; the sync cleared itself at 13:36.
**The rule this earns: never characterise a value that is visibly truncated, stale, or that you
have not read in full. Query it first.**

## A prover that passed vacuously, caught by re-running it
`prove-grounding-cloud` passed for the agent and FAILED under the main session. `loadLanes()`
caches on `(path, mtimeMs)`, so two writes inside one millisecond look identical and the fake
endpoint was never restored: the error, quota and timeout cases never ran, and the check said PASS
in both shapes. Now a fresh lanes file per call plus assertions that make a vacuous pass fail by
name. 9 of 10 rounds red before, 5 of 5 green after. **Re-running an agent's own green is what
caught it.**

## NAMED AND NOT FIXED
- **The ear.** Speech to text mangled his words twice: "The booker is an engine version in Dublin"
  and, on the phone, "The book is an interesting version". Untouched.
- **LOGOI takes 47 s per question** because it loads the brain into every one. Measured the same
  question both ways: **46.8 s with context (first word 9.7 s), 4.8 s without**. That is why his
  phone showed Safari's own red "LOAD FAILED": the connection outlived the answer. LOGOI itself
  was healthy and his voice never left the laptop.
- `loadLanes()` can serve a stale table in production on two same millisecond writes.
- `settleGroundingChecks` is not wired into shutdown, so a check in flight dies without its row.
- `grounding.md` hands a small model a ready made excuse; llama3.2 pasted "The brief gives an
  average score" onto a brief with no score.
- `norm()` does not split "19euro" into two tokens.
- **Build also uses the cloud lane** when the switch is on. King has not ruled on that.

## 6.5 CLOSED, 15:00, AND STAGE 6 WITH IT
After the engine was restarted at 14:46 onto the fixed code, he ran it again and closed it himself.
- **Laptop:** both briefs spoken, the instant reply heard twice, the real answer heard, including a
  `not_ready` refusal quoting his own sentence.
- **Phone**, on the deck at `:8443` over Tailscale, NOT LOGOI: he spoke "Create an agent, make me
  money.", heard the instant reply, then heard "I've looked at your brief. It's ready to build
  whenever you are." at 14:58:43, **spoken in 5,503 ms**. His words: **"Heard it over phone"**.

**THE NOTES LEAK GUARD FIRED ON LIVE TRAFFIC, 40 minutes after it was committed.** That phone
mission (`4c918f1b`) made TWO model calls: the first answer came back with "TikTok Creator Rewards,
10k followers, 100k views, 30 days", none of it in his brief. The guard caught it, discarded it and
re-asked his brief alone, costing 30.5 s rather than another 5 minutes. The second answer is the
plain one he read. **The fact checker then SKIPPED correctly**: "no new specific in the output,
nothing a tracer could catch". Both fixes working on real traffic, unprompted.

**One thing seen and not raised with him:** that verdict's `verdictReason` says "audience not
specified in the brief, needs confirming" and the verdict is still `build`. A verdict that names its
own gap and passes anyway is worth a look. NOT a defect yet, just unexamined.

**NEXT: Stage 7, and it is a blank page.** `progress_board.py:120` reads
`Stage("7", "5D, KD Robot, beta", "not_started", "Not begun.")` with NO iotas written anywhere. The
move is 7.0, writing its steps first, exactly as 6.0 opened Stage 6, from his own 29 Aug words:
"5d is the combination of it all, interacting fully immersive like gta 6, controllable via vpn on
phone or app". The base already exists: AUREO, his approved Three.js city, 520 lines, 60fps on a
real phone, with EDEN as the live data behind it.
See [[project_kd_robot_stage6_console_2026-09-06]] and [[project_diagnose_method_scope_2026-09-12]].
