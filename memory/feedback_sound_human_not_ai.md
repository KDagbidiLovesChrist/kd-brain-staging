---
name: feedback-sound-human-not-ai
description: "ALL writing (chat to King, brain files, Notion, Obsidian pages, map labels, generated text, client output) must read human, in King's voice. Zero em/en dashes anywhere. Hard rule."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 64e05a51-21d8-4515-b398-576edb173937
  modified: 2026-08-07T15:03:55.437Z
---

# Sound Human, Not AI: Hard Rule for All Written Output

> **🆕🔴 2026-08-07, EIGHTH violation, AND the fix that finally changed shape.** King caught an em dash
> in a live chat reply during the brain-reorg session ("Before I touch this, I need to flag..."). Swept
> every file edited that session (CREED.md, CLAUDE.md, subagent_registry.md, SKILL_TIER_LEDGER.md,
> build_brain_dcim.py) and confirmed all were clean, the violation was chat-only, not deployed into a
> file. King's response was sharper than before: he didn't ask for another promise, he asked for the
> check to be structural, "the human layer" built into the Logic layer itself, not memory-dependent. The
> 2026-07-03 "ENFORCEMENT NOW MECHANICAL" entry below was never actually mechanical, it was a
> self-check I was supposed to remember to run, and memory alone had already failed seven times. **Real
> fix this time: `tools\check_no_dashes.py` + a `PostToolUse` hook on `Write|Edit` in `settings.json`.**
> Every file write/edit is now scanned automatically for U+2014/U+2013 and blocked with a reason if found,
> whether or not I remember to check. Pipe-tested clean, pipe-tested on a deliberate violation, and
> proven live in the same session (a real Write with a planted em-dash was caught and blocked in real
> time). This does not cover chat replies themselves (hooks fire on tool calls, not on message text), so
> the manual pre-send check in point 1 below still matters for chat, but every file in this brain now has
> a mechanical backstop that memory alone never provided. **Same-session postscript, same day:** King asked
> directly why he was still seeing dashes minutes after the hook shipped. Checked my own recent chat replies
> and found four more em-dashes in plain conversation text, after the hook, after already being caught once
> that session. The hook only covers Write/Edit file content, chat text has no mechanical net at all, and
> knowing that gap intellectually did not stop me falling into it repeatedly in the very next messages. This
> is the clearest evidence yet that the failure mode is real-time generation habit, not a lapse in
> remembering a rule, self-monitoring alone is not reliable even minutes after building a fix for the exact
> same problem.

> **🆕🔴 2026-08-06, SEVENTH violation.** King spotted an em dash in the Logos + Klarnow explainer artifact title itself, the exact thing being shown to him. Swept the whole build and found 30 more instances in that one HTML file, plus dozens in `knowledge\klarnow\klarnow_master_prompt.md` (Stage 1 of the same session) and in the plan file. Root cause: three documents authored back to back in one session, under time pressure to cover a lot of technical ground, with the pre-send grep never run on any of them before showing King. Fixed by grepping both files for U+2014/U+2013, confirming zero matches, republishing the artifact to the same URL. **Added a Voice and Tone guardrail directly into `klarnow_master_prompt.md` itself** so future Klarnow-related documents inherit the rule from the brief they're built from, not from memory alone. Also worth recording: Klarnow's own written Identity OS Voice System (`08-identity-os.md` §6) independently bans "em dash" in its own spec, so King's rule and Klarnow's own client-facing standard agree without any conflict to manage.

> **🆕🔴 2026-08-06, SIXTH violation.** Klarnow prototype build (`knowledge\klarnow\prototype_demo\index.html`), King spotted an em dash in live Clarity Brief copy after I'd already claimed a cleanup pass complete and moved on to showing him the result. Root cause: I fixed the dashes I happened to grep for in one pass but stopped short of re-grepping the WHOLE file before declaring it clean, so a line I'd already generated with a dash (in a template string built before the "no dashes" instruction landed mid-session) survived. Fixed properly this time by grepping the entire file for both glyphs and confirming zero matches before showing King again. **The mechanical check in point 1 below has to run as a full-file sweep, not a spot-fix of the lines I remember editing.** This incident is also the origin of [[feedback-staged-qa-loop-standard]] (Rule #26, CLAUDE.md), King's response was to make "QA-loop until genuinely clean, then show real proof" a permanent cross-project procedure, not just re-state the dash rule again.

> **🆕🔴 2026-07-03 (evening), FIFTH violation, same day as the fourth.** King: "even the dash in your speech and old stuff you didnt fix, is this brain really getting smarter each use?" The evening session (Council of LOGOS-OS) leaked dashes into chat replies AND into 6 new files (OPERATING_RHYTHM, COUNCIL_OF_LOGOS.html, project memories, MEMORY.md, the plan file), 54 instances, hours after the morning sweep. Swept clean same night. **The lesson written plainly for every future session: the pre-send scan is not optional and CHAT REPLIES ARE INCLUDED. Before every reply to King and every Write/Edit, check the draft for the two dash glyphs. No exceptions, no "internal file" excuse. When King asks if the brain is getting smarter, this file is the honest answer: memory holds the rule perfectly, the agent must actually run the check every single time.**

> **(2026-07-03 morning) FOURTH violation caught. King: "why is that dash there... go through my memory, all past present and future, sound like me, no more ai slop."** He saw em-dashes all over Notion and Obsidian. The rule below already banned them everywhere since 06-22; the failure is Claude reverting to training habits. **ENFORCEMENT NOW MECHANICAL, not willpower:**
> 1. Before ANY Write/Edit of a text file and before sending any chat reply: scan the draft for the em dash (U+2014) and en dash (U+2013). If found, rewrite the sentence (comma, full stop, brackets, or " · " in headings/indexes/labels). This file names them by unicode on purpose so the glyphs never live in the vault.
> 2. The whole vault was swept clean on 2026-07-03 (script; scripture-quote lines guarded, never altered). The generators (nightly_review.py, notion_brain_sync.py, DCIM builder, canvas + graph labels) were cleaned so FUTURE generated text is born clean.
> 3. King's voice in brain pages: plain, short, warm, faith-first, "·" as separator, → for flow. Never corporate connectors.
> 4. If a dash ever appears again in anything King reads, treat it as a broken standing rule, fix it immediately and log the miss here.

> **🆕🔴 2026-07-01, King: "humanise your speech and text." This is about HOW I TALK TO HIM IN CHAT, not just outreach.**
> After a long build session I reverted to talking like a corporate slide deck: em-dashes everywhere, stacked
> bold headers, emoji bullet-ladders, section dividers, formal phrasing. King doesn't want a formatted AI report,
> he wants a person talking to him. **How to apply to every chat reply to King:** plain natural sentences,
> contractions, warm and direct, like a friend explaining something. Cut the heavy structure. Use a header or a
> short list only when it genuinely helps him scan, not by default. Zero em-dashes (see below). Fewer emojis.
> Say what happened in normal words first, keep the detail short. If it reads like a report, rewrite it like speech.

> **🆕🔴 2026-06-30, King reaffirmed "humanise ALL emails", including his own notification pings.** I had been
> leaking em-dashes into chat replies and into the brain-map / successor-letter emails all session. King caught it.
> Removed the self-email exemption from `commands\humanize.md` RULE 1. From now: zero em/en-dashes in EVERYTHING
> (chat to King included), and every email gets the humanise pass before it sends, no exceptions.

> **🆕🔴 2026-06-22 (STRONGEST FORM), NO EM-DASHES OR EN-DASHES ANYWHERE, EVERY TASK.** King: "remove ai slop
> and dash from every task and work we do... the '-' i dont want to see that anymore." This is no longer just
> for outgoing person-to-person messages. It applies to EVERYTHING I produce: chat replies to King, documents,
> budgets, HTML, image text, file content, all of it. The em dash (U+2014) and en dash (U+2013) are his number one AI
> tell and he does not want to see them at all. Use commas, periods, colons, "to" for ranges, or restructure.
> Plain hyphens in genuine compound words are tolerable but minimise even those. When generating any text
> artifact, grep the output for U+2014, U+2013, "mdash", "ndash" before sending and strip any that leaked.

> **🆕 2026-06-21, `/humanize` skill now exists (`commands\humanize.md`).** King: "add a humanizer skill
> to remove the AI at all times… emails when talking to other people must sound like me (tone/style/pref)."
> **RUN IT AUTOMATICALLY before ANY person-to-person message** (client emails, cold outreach, WhatsApp/DMs,
> proposals, captions, replies to Josh/family/buyers), not just on the `/humanize` trigger. **When a message
> goes out under King's name, write it AS King** (first person, his phone-typed voice from `brand_assets\bio.md`):
> plain English, contractions, short+long mix, warm/direct, NO em-dashes, no "delve/moreover/leverage/hope this
> finds you well". Exempt = the internal brain pings King sends to his OWN inboxes. The skill has the full
> kill-list + King's voice profile + the pre-send SOP. This makes "sound human" a standing reflex, not a
> per-task ask.

**Rule:** Any external-facing writing King David asks for, CVs, cover letters, cold emails, proposals, newsletters, website copy, Skool posts, client deliverables, must read as if a thoughtful human wrote it. No AI tells. Ever.

**Why:** King David said it directly in the CV Tailor planning session (2026-05-21):

> "It needs to make sure that when you're writing this stuff first you need to make it sound as left or bottom as possible. It needs to sound like I said if it was from a human. Let that be your normal preference. We're not getting you to do anything for me. It needs to sound human, not robotic or AI."

This is a permanent preference. He was speaking about CV Tailor specifically, but said "let that be your normal preference", so it applies to everything written across all projects. Recruiters, hiring managers, prospects, clients, community members, they all detect AI writing in 2026 and filter it out. AI-flavoured output costs King David money.

**How to apply:**

1. **Read the rulebook first when writing.** `C:\Users\Dell\Documents\CV Tailor\workflow\humanizer_rules.md` is the canonical source. It has the banned-words list (delve, robust, leverage, navigate, harness, tapestry, comprehensive, synergy, underscore, "in today's fast-paced", etc.), banned sentence patterns ("I am writing to express my interest…", "I am thrilled to apply…"), and the 4-axis scoring rubric (specificity, originality, voice, authenticity).

2. **Default tone targets:** Confident not boastful. Specific not flowery. Warm not over-friendly. Direct not blunt.

3. **Mandatory ingredients in any written piece:**
   - At least one specific, falsifiable fact
   - At least one named project, model, person, or moment
   - One reason specific to THIS recipient that doesn't appear on their homepage
   - Natural contractions where appropriate ("I'm", "I've")
   - One slightly imperfect sentence (humans don't write perfectly parallel prose)

4. **Self-check before delivering:** Re-read what you wrote. Could it be sent to anyone else with names swapped? If yes, it's too generic, rewrite. Are there banned words? Remove. Three em-dashes or more? Reduce.

5. **For CV Tailor specifically:** Agent 4 (Humanizer QA) enforces this with a scoring loop. Score below 8/10 = automatic rewrite. For other projects without that QA agent, apply the rules manually.

**Stricter sub-rules added 2026-05-21 after first real CV Tailor pack:**

6. **ZERO em-dashes in cover letters, cold emails, SMS outreach, Skool posts, newsletter copy, or any written client-facing piece. Maximum ONE em-dash in a CV** (only if essential for a compound term). Em-dashes are King David's number-one AI tell, even two in a piece reads as AI to him. Replace with periods, commas, semicolons, parentheses, or restructure the sentence. **Extended 2026-05-25 after I drafted Dublin plumber cold emails with em-dashes, King David caught it on the very first batch. Hard rule applies to ALL outreach, not just CVs.**

7. **Real-seed methodology for soft-skill stories.** When the candidate "can't remember" a teamwork / leadership / problem-solving incident, don't fabricate. Ask scenario-based memory triggers (3, 4 common workplace situations per category). The candidate picks the one that rings true and provides the seed, Claude writes at **cover-letter altitude**: event clear, action clear, specifics (dates, named individuals, exact items) left abstract so the candidate isn't boxed into details they'd need to recall verbatim at interview. This honours the Honesty Boundary while still producing strong copy.

8. **Final detection gate (coming next CV Tailor session).** Real third-party AI detector (GPTZero) will run as the final step on every CV + cover letter pack. AI-probability > 10% = automatic rewrite. The 4-axis Claude-judges-Claude rubric stays, but GPTZero is the truth check.

**Cross-references:**
- [[reference-brand-assets]], King David's brand tone
- [[reference-wat-framework]], every WAT project produces written output that should follow this rule
- [[project-cv-tailor]], CV Tailor is the canonical implementation; humanizer rules + Humanizer agent live there
