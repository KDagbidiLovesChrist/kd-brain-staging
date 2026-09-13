# Stage T · the brain learns where it is standing · 9 September 2026, evening

King's ruling, in his words: **"scrub the three lines and make the retrievals travel-aware, local
yes, cloud no, which the logos engine's already does for prompts and my Python side does not."**

Satellite of [project_price_parity_2026-09-09.md](project_price_parity_2026-09-09.md), which
records the guard finding that led here.

---

## The problem, and why the honest answer an hour earlier was so poor

He asked whether a flagged file should be shut to models or left open. Reading the code gave a
worse answer than expected: `brain_retrieval._is_forbidden` says **"Every file, every time"**. One
setting. A file was readable by every model alive or by none.

So to keep three lines away from a cloud vendor he would have had to make **LOGIC-A and LOGIC-B go
blind** to a whole day's build record. Measured, not assumed, by running real queries first:

```
[YES]  how does the spend gate decide whether to allow a paid call
[ no]  what is LOGIC-B and what runs on it
[YES]  why did the engine keep running from the old brain      <- ranked 1st
[YES]  what is the return path and how do recipes work          <- ranked 1st
[ no]  how do I pray the morning rule
```

That file is load-bearing for the compound memory he calls the most important thing in the product.
Shut was the wrong tool; the exposure was three lines, not 776.

---

## T0 · the scrub (commit `89d175b7`)

The record named the six documents inside `the-truth`. Not their content, their **filenames**, which
is a map to his most private material riding along on any engineering query that matched.

**The file already contained the rule it was breaking.** Further down it records, as a real catch
before `kd-infra` left the machine: *"A rejection list that names a file reveals the file exists,
which defeats the gate that rejected it."* Written about a manifest; it applied here word for word,
including to the sentence that said it.

Three edits, each keeping the fact and dropping the map. Verified after: each of the six
scrubbed terms returns **zero** occurrences. They are not repeated here, for the same
reason they were removed from there. Guard class green, 53 of 53.

**Caught in this very file on review, which is the point.** The first draft of this record
listed those six words in order to say they were gone, putting the map straight back. The
manifest made the identical mistake earlier the same day. A rule is easy to state and easy
to break in the sentence that states it.

**Flagged, not acted on:** the sync guard's `METHOD_MARKERS` would have caught **neither**
file. It looks for method words, and these are faith filenames. Both leaks were found by
hand. Widening that marker list would make the guard stricter, which is the safe direction,
but it would likely turn several existing files red at once, so it is King's ruling rather
than a tidy-up.

---

## The build, modelled on his engine rather than invented

The engine's `enforceTravel()` in `src/lib/prompt-registry.ts` already does this for prompt records,
and its own comment calls it *"the lane rule as code, not just a label"*. The Python side got the
same idea, the same word, and the same fail-closed default.

### T1 · a middle tier, with the strict list untouched

`logoi_gate.py` gains `LOCAL_ONLY_PATHS` beside `NEVER_LEAVES_PATHS`. **Nothing was moved out of
the strict list**, which was the one mistake this stage could make, and that is proven rather than
promised: the block was extracted from `git show HEAD` and compared, **BYTE IDENTICAL: True**.

Seeded deliberately small, two entries. Widening it is a ruling, not a tidy-up. **Candidates raised
for King and NOT added:** `knowledge/harness_map` (names every door and its live state),
`memory/project_logic_binder`, `memory/project_kd_robot`.

### T2 · the guard asks where it is standing

`resolve_travel()` resolves the node and the caller, **stricter wins**:

```
  no env, caller says nothing      -> cloud      no env, caller says Local        -> local
  no env, caller says local        -> local      node=local, caller silent        -> local
  no env, caller typo LOKAL        -> cloud      node=cloud, caller says local    -> cloud
  no env, caller empty string      -> cloud      node=cloud, caller silent        -> cloud
```

A caller that forgets to say **loses an answer; it never leaks one.** A rented node overrules any
request, which is what makes T5 work for free.

### T3 · enforce on the way OUT, not at index time

**The trap the whole stage turns on.** The FTS5 and hybrid rungs filter while *building* their
sqlite index, and that index is built once and searched by every lane. Check travel only at build
time and a local-only file sits inside a file that a cloud question then searches, while every
other check in the stage still passes.

So the tiers are enforced in two different places on purpose: never-leaves at index time, because
it should not be in the corpus at all; local-only on the way out, because **the corpus is shared and
the question is not.**

Proven against a rebuilt index, not a fixture:

```
  sections of the local-only file sitting INSIDE the shared index: 25   <- there on purpose

  Q: why did the engine keep running from the old brain
     local   5 hits, present: True
     cloud   5 hits, present: False
  caller says nothing: False  <- fails closed
```

**Cloud still gets a full five.** The TF-IDF rung skips inside its ranking loop; the two sqlite
rungs over-fetch, filter, then truncate. A quietly shorter answer is how someone concludes the brain
got worse rather than narrower.

### T4 · the door the engine actually knocks on

`/api/retrieve` is how the Logos engine asks the brain for context, so it is the one door where a
local-only passage could walk into a cloud prompt. It now reads `travel` and **reports the lane
back**, so a narrowing is visible rather than silent. Proven through the real handler:

```
  travel=local   HTTP 200  lane: local  hits: 5  engine_and_hearts: True
  travel=cloud   HTTP 200  lane: cloud  hits: 5  engine_and_hearts: False
  not specified  HTTP 200  lane: cloud  hits: 5  engine_and_hearts: False
```

Worth recording: because T2 made the guard default to cloud, the belt-and-braces `_is_forbidden`
already sitting at that boundary **began failing closed the moment T2 landed.** T4 made that
explicit instead of accidental. The local chat now passes `travel="local"` and keeps everything it
had.

### T5 · Oracle says what it is

LOGIC-B is a rented box, so the librarian sets `LOGOS_TRAVEL=cloud` itself rather than trusting
whoever wrote the systemd unit. It serves the curated binder, but *"the guard was applied upstream"*
is the same reasoning that let a manifest leak filenames earlier the same day.

```
  LOGOS_TRAVEL before importing the librarian : None
  LOGOS_TRAVEL after                          : cloud
  resolve_travel('local') -> cloud   <- the node overrules the request
```

### T6 · the prover

`tests/unit/test_travel_retrieval.py`, **26 of 26**, added to `tests/real_coverage_gate.sh` in the
same commit per the standing rule, along with coverage on `brain_retrieval` and `logoi_gate`, which
hold the guard this stage rewrote and **were not measured before** while the two rungs built on them
already were.

It tests the ways this gets got wrong, not the happy path: the strict list still refusing **both**
lanes so the middle tier cannot become a way around it, the two lists never overlapping, a
non-string never crashing or opening the guard, the index still built at the local tier (regress
that and cloud stays safe while **local silently goes blind**, the failure that looks like success),
every rung carrying the argument so none is an open door beside a shut one, and the over-fetch so
filtering cannot shrink a cloud answer.

---

## What it buys, plainly

Before: to keep three lines from a vendor, blind both his own hearts. After: **LOGIC-A and LOGIC-B
read everything they always did, and the cloud gets the narrower view.** Compound memory kept
without paying for it in secrecy.

**Coupled to a decision still open.** The engine mostly runs local today, so little of this travels
yet. His own record says the last near miss survived because *"the engine was running a local model,
which is luck rather than a guard."* The moment `routeChain` is wired into `ai-gateway.ts`, ordinary
engineering questions start reaching cloud vendors. **Stage T is what makes that switch safe to
throw.**

---

## Still owed

- The three candidate paths above need his ruling before they go in the middle tier.
- The FTS5 index on disk was **five days stale** (built 4 Sep, 4,848 sections; rebuilt to 4,730).
  Nothing schedules a rebuild. Worth a task, since a stale index quietly answers from a dead brain.
- The hybrid rung's vector lane was not exercised end to end here, only its signature and its
  over-fetch; it needs sqlite-vec and a live embed to run.
