---
name: project-paintpots-cosmic-colours
description: "King's college web design brief (PaintPots/Cosmic Colours, Bootstrap 5 site + report + screencast, institution never named in the brief itself), decomposed into a 30-frame tracking system so King can check his own graded work against the rubric. Tracking tooling only, not a ghostwritten submission."
metadata:
  node_type: memory
  type: project
  originSessionId: 5f88ab7f-d0a8-4a34-94fa-6668952617bb
  modified: 2026-08-28T10:11:08.058Z
---

# PaintPots · Cosmic Colours · assignment tracker

**Status: 🟢 CORE DONE (corrected 2026-08-27). The 30-frame brief and the network diagram are both live. What's left is the standing-habit note and King's own answers to the brief's open questions, not the assignment work itself.**

## What this is
King emailed himself (Yahoo → Gmail, 2026-08-26 03:45, thread `1a03c2c5f1f28445`) a college web
design brief: a fictitious paint company site (Bootstrap 5), a 500+ word written report, and a
3 to 5 minute screencast, graded 60/20/20. Genuinely graded, "like an actual university exam
thesis" in his own words. **The brief itself never names the institution or module, that detail
was wrongly assumed as "TU Dublin" in an earlier version of this note, based on King's own
LinkedIn credential line on an unrelated email, not the brief itself. Corrected here, not stated
as fact anywhere else in this file.** This project is tracking and analysis tooling so he can check his own
work against the brief's exact wording and the 7-point rubric, it is explicitly not a ghostwritten
submission. The brief's own line stands: *"The logo, background image, and all other content on
the site must be your own original creations."*

## What's built and real
- **`projects\paintpots-cosmic-colours\`** scaffolded via `tools\new_project.py`, standard WAT
  structure. **`ASSIGNMENT_BRIEF.md` landed** (18KB, the full 30-frame writeup, on disk in the
  project folder, MANIFEST marks it done).
- **The network diagram**, published: https://claude.ai/code/artifact/185ec477-35ca-47b4-9f5e-2fd9c5256514
  30 nodes (23 build steps + 7 grading criteria), real dependency lines (which build step feeds
  which criterion), Step 8 flagged red (a genuine ambiguity in the brief), Step 16 shown broken
  (Step 3 is missing from the source entirely).
- **The method, proven and now extracted as a skill.** `commands\frame-by-frame-decompose.md`,
  T2 in `_ops\SKILL_TIER_LEDGER.md` (scouted 2026-08-27 via `/find-skills`, real convergence against
  GitHub Spec Kit and ThinkUpfront/Upfront, both independently landing on the same shape this method
  already used). Every frame carries 3 layers: Process
  (King's own 0→9→0 loop from `_ops\LOGOS_0_MATHS.md`, used as a status marker only, nothing
  extrapolated past what his file states), Foundation (0→1, does the output exist), Quality (his
  60/70/80/90/100 = stage 1 to 5 ladder, worked per frame, honest binary where no real gradient
  exists, marked **x** where the brief itself is unresolved rather than forced). Each quality stage
  checked 3 independent ways (textual match, rubric mapping, plausibility), not asserted once and
  relabeled "3/3."
- **4 real defects found in the brief itself**, checked against the actual email text: Step 3 is
  missing entirely (jumps Step 2 to Step 4), Step 2's own numbering restarts after item 9, "Step 6"
  is used twice for two different things, and "the two featured projects" (Step 2 item 6) doesn't
  match the rest of the brief's "4 colours" framing, still unresolved, King's to state.
- **`tools\yahoo_inbox.py`**, new, general read-only Yahoo IMAP reader (the two existing Yahoo
  tools are keyword-filtered, loans-only and Klarnow-only). Built this session to find the brief
  in the first place.

## What's not done yet
Corrected 2026-08-27, checked directly against the real files: two claims that used to live here were
wrong. `ASSIGNMENT_BRIEF.md` DID land. `/find-skills` WAS actually run (2026-08-27), a real scout
against GitHub Spec Kit and ThinkUpfront/Upfront. `commands\frame-by-frame-decompose.md` is built and
registered at T2 in `_ops\SKILL_TIER_LEDGER.md`, not `subagent_registry.md`, checked directly: that
file is only the 12 standing-army dispatched agents, not a skill index, so this skill correctly has
no entry there.

Genuinely still open:
- The `memory\feedback_frame_by_frame_decomposition_habit.md` standing-habit note, now written, see
  [[feedback_frame_by_frame_decomposition_habit]].
- The skill's own climb from T2 to T3 needs King's yes plus a real `/qa` run, not assumed.
- The project's own open questions below, his to resolve.

## Real, checked open items (his to resolve, not guessed at)
- "The two featured projects" (Step 2 item 6): what does this actually refer to?
- Adobe billing failed a third time (23 Aug, PayPal), which blocks the Photoshop work the brief
  requires (the logo, background, and 4 colour images all need it).
- The brief itself never states a deadline or module name.

## Governance notes from this build, useful for next time
- King's own maths file (`_ops\LOGOS_0_MATHS.md`) says four times, in its own words, "King derives,
  Claude records." The 0-9-0 loop was reused exactly as stated, nothing past that was invented.
- Encryption (the substitution layer in that same file) is explicitly Uncle Tony's hand, not
  Claude's, per `memory\feedback_king_derives_maths.md`. Declined to build a new cipher layer when
  asked, offered to cite existing substitutions instead.
- DeepSeek came up as a possible model to route through. Declined: unvetted (no gate, no audit
  trail the way OpenRouter/NVIDIA got), and this session's own content (faith/OSB discussion)
  is exactly the kind the 25-Aug "faith excluded, no exceptions" rule already covers.
- n8n came up (real, already installed, v2.20.9, `n8n-mcp` in settings.json) as a "connect every
  skill" idea. Deliberately kept out of this build, it's a whole-brain architecture decision, not a
  PaintPots sub-task. King agreed to keep it separate.

## The pacing this session actually needed
King disclosed a brain injury mid-session and asked directly for coordination support: stop and
break a step down further whenever it doesn't land, verbal AND visual together, nothing left
implicit. This matches what's already on file elsewhere about Rules 18 and 26 being an
accommodation, not a style preference (see the guarded personal record already in `_private\`,
not duplicated here). Two `AskUserQuestion` calls this session came back as a bare "." rather
than a real selection, worth noting as a possible friction point with that UI specifically, plain
text and small real actions (like scaffolding the folder) landed better than another multiple
choice prompt in the moment.

## Next step, exact
`ASSIGNMENT_BRIEF.md` is done. The real next step is King's own: answer the "two featured projects"
question, clear the Adobe billing block, and confirm whether he wants the skill pushed from T2 to T3
(needs his yes plus a real `/qa` run).

Related: [[feedback_frame_by_frame_decomposition_habit]] (the standing-habit note, written 2026-08-27) ·
`_ops\LOGOS_0_MATHS.md` (guarded, King and Uncle Tony only) · `memory\feedback_king_derives_maths.md`.

**⚠️ Separate track, do not conflate (28 Aug):** [[project_paintpots_samson_website_build]] is a
different piece of work, a full working website built and delivered to King's friend Samson, not
King's own tracking-only approach described above. Different session, different purpose.
