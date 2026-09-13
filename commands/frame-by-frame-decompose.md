# /frame-by-frame-decompose · Turn a Dense Brief Into a Checkable Frame Register

**Trigger:** `/frame-by-frame-decompose <document>` OR "break this brief down," "decompose this spec,"
"turn this contract into something I can check my work against," "no iota missed"
**Purpose:** Take an already-written, dense instruction document (a brief, a contract, a spec, a set
of grading criteria) and turn it into a numbered frame register, each frame carrying a real quality
ladder checked three independent ways, so the requester can measure real work against it later. This
is a document-intake front end for `commands\consult_living_spec_template.md`'s Requirements
Register, for when the spec already exists as text rather than being built live in an interview.
Proven once, in full, on a real 30-frame college brief (2026-08-26).

> Validated against real outside prior art via `/find-skills` (2026-08-27): GitHub's own Spec Kit
> calls its quality-check step "unit tests for English," a sharper name for what Step 2 below
> already does. ThinkUpfront's Upfront scores spec coverage hit/partial/miss/unknown, independent
> confirmation that marking a genuinely unresolved item as its own state (not forcing a number) is
> the right shape, not a shortcut. Neither tool does the reverse-engineer-an-existing-document
> version of this, that part stays original to this Skill.

---

## STEP 0 · Read the whole document first, don't skim
Read the entire source document before decomposing anything. Note its own structure as given
(its own numbering, its own section breaks), don't impose a cleaner structure on top of a messy one
yet, that comes later, and only as a flagged correction, never a silent one.

## STEP 1 · One frame per source step, numbered to match the source's own order
A frame = one instruction, one requirement, one line item, in the order the source gives them.
Where the source nests (a numbered sub-list inside a numbered step), the frame ID nests too
(`2.1`, `2.2`...), matching the source's own depth, not flattened for tidiness. Every frame quotes
the source's exact wording, in full, not paraphrased, the quote is what makes the frame checkable
later.

## STEP 2 · Three layers, on every frame ("unit tests for English," per Spec Kit's own naming)
- **Process**, 0 to 9 to 0: not started, in motion, executed. Honestly `0` for every frame until
  real work actually happens, never marked ahead of the fact.
- **Foundation**, 0 to 1: does this frame's output exist at all yet, binary, no partial credit.
- **Quality**, a 5-stage ladder if the source genuinely supports 5 distinct levels, or **honestly
  binary** if it doesn't (a filename either exists or it doesn't, there's no 70% version of a folder
  name). Never force 5 fake bands onto a task that's really pass/fail. If the source document states
  its own percentage weighting or grading bands, use those exact numbers as the ladder's rungs
  instead of inventing a generic one.

Each quality stage gets checked three independent ways before it's trusted, not asserted once and
relabeled "checked":
1. **Textual**, does this stage's claim trace to an exact phrase in the source.
2. **Rubric**, does it map to one of the source's own stated success criteria, if it has any.
3. **Plausibility**, would someone reading the source cold actually recognise this as accurate.

All three agreeing is a real pass. Where they don't agree, or where the thing being measured is
itself undefined in the source, mark the stage **x** (an unresolved variable, not a guessed number),
matching Upfront's own "unknown" state, a fourth honest option next to hit/partial/miss.

## STEP 3 · Find and flag the source's own defects, don't quietly fix them
Real documents have real mistakes: a missing step number, numbering that restarts, a term used for
two different things, an instruction that doesn't match the rest of the document. Record every one
found, quoting exactly where and how, and leave it flagged rather than silently resolved. A version
of this that "cleans up" the source's own mistakes is less accurate, not more, it stops being a
faithful register of what was actually asked.

## STEP 4 · The TODO, generated from the frames, not written twice
Unpack each frame's Stage 1 into "the first thing to do" and its Stage 5 into "what done well looks
like." A frame with multiple distinct outputs (four images, five report sections) becomes multiple
parallel TODO lines, one per output. A frame with an unresolved (x) stage stops its TODO line at the
last resolved stage, everything past that is marked not-actionable until the source's own ambiguity
gets resolved by the person who owns the document, never guessed at here.

## STEP 5 · The visual half, when one is wanted
A flat 30-plus-frame list is hard to scan. Where a diagram is wanted, draw the frames as a network,
not a grid: the source's own sequence as the spine, plus a second layer of lines from each frame to
whatever end-state criteria it actually feeds (a grading rubric, an approval gate, a sign-off list),
pulled from the real Step 2 rubric mapping, never decorative. Flagged defects get a visibly different
line style (dashed, a different colour), so the one open item in a large register is visible in the
shape of the diagram itself, not buried in text.

## Boundary, worth stating plainly every time this runs
This Skill produces analysis and tracking tooling, a way to check real work against a real source.
It does not produce the actual deliverable the source document is asking for. If the source document
has its own originality or authorship requirement (a graded assignment, a client's own creative
brief), that requirement still applies in full, this Skill never substitutes for it.

## WAT
**W** = this file. **A** = Claude reads the source, reasons frame by frame. **T** = Write/Read for
the register itself, Artifact for the network diagram when one's built. **S** = `/frame-by-frame-decompose`.

**Worked example:** `projects\paintpots-cosmic-colours\ASSIGNMENT_BRIEF.md`, the full 30-frame
register this method was proven on, referenced here, not duplicated.
