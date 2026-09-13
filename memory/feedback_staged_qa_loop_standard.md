---
name: feedback-staged-qa-loop-standard
description: "Permanent rule (2026-08-06, Rule #26): build multi-step work in stages, QA-loop each stage until clean, show King the real thing, wait for his yes before the next stage. Applies to every agent dispatched, not just the main thread."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: f07ca44d-f726-4af4-bdde-3ce6d509cb96
  modified: 2026-09-03T20:00:54.442Z
---

# Build in stages, QA-loop each one, show real proof, wait for the yes

Set 2026-08-06 during the Klarnow prototype build, right after a sixth em-dash violation
(logged in [[feedback-sound-human-not-ai]]) got caught mid-build. King's instruction was
explicit: **"we will follow this proceedure with all agents and every task we do not just this
project but for the claude.md."** Now Operating Rule #26 in the master CLAUDE.md, permanent
across all projects. This file covers what's genuinely new beyond the existing dash/QA rules,
staging discipline and full-path testing, not a restatement of them.

## The rule
1. **One stage at a time.** For any build with more than one deliverable piece (a prototype with
   multiple screens, a deck with multiple slides, a multi-page site), do not build all of it
   silently and reveal it at the end. Finish one stage, stop, show it, get the yes.
2. **Test the full state space, not just the happy path.** A couple of manual clicks through one
   branch is not enough for anything with branching logic. Walk every reachable path
   programmatically where feasible and confirm zero errors across all of them, the way the
   Klarnow diagnosis tree's 108 branches were swept in one `evaluate()` call rather than
   spot-checked by hand.
3. **Show the real thing, in his own browser.** Open it for him (launch the URL directly),
   don't just paste a link and hope, per [[feedback-show-screen-while-browsing]].
4. **If King previews ahead on his own, address that feedback immediately**, even if that stage
   wasn't "officially" reached yet. Don't insist on strict sequencing over responding to what he
   actually just told you. Default posture is still build, prove, ask, then continue.
5. **Every dispatched agent follows the same standard**, not just the main thread. Brief every
   background/subagent explicitly with the no-shortcuts instructions (test your own output before
   reporting done, zero em dashes, no generic AI-marketing language, per
   [[feedback-sound-human-not-ai]]). If King pauses parallel background work to enforce
   sequencing, don't relaunch it until asked.

## Full-file sweep discipline (the specific gap that caused violation six)
A partial dash-cleanup pass, fixing only the lines touched in one grep, is not the same as a
clean file. Before declaring any text clean: grep the WHOLE file for both dash glyphs, confirm
zero matches, only then show it. Doing this once at the start of a session doesn't cover text
generated later in the same session under a different instruction.

## Why
King's own words: he wants it so that "when I show them they are like wow he acc did that for
every step." The proof standard is the deliverable, not just the code. Pairs with the pay-grade
standard ([[reference-wat-framework]] Rule #25), a build that's technically functional but
visibly rough still undercuts it.

## How to apply
Default posture on any non-trivial, multi-piece build from now on. Break the work into an
explicit todo list of stages up front, mark each in_progress/completed only once actually proven
working via a real test (not assumption), and treat "show King the real artifact and get a yes"
as a required step in the loop, not an optional courtesy at the end.

## The living progress board is the concrete mechanism (3 Sep 2026, KD Robot)
King's instruction, verbatim: **"be updating progressandplan board each time todo is done."** For
any project that has a living board generated from probes (KD Robot's `tools\progress_board.py`,
republished to the same claude.ai artifact URL and served live on the Vault), rebuild and show
that board the moment each todo item closes, not batched at the end of a stage or a session. This
sharpens rule 1 above into a specific, repeatable action: a todo closes, the board rebuilds from
probes, gets republished, gets shown, before starting the next todo. Applies inside a background
build too (a workflow or dispatched agent finishing one piece is a todo closing).

**Why:** this is the same "show the real thing, wait for the yes" discipline, but for a project
with its own generated board, the board itself is the proof, so every todo becomes a proof screen
rather than only stage boundaries.
