---
name: logos-engine-fixes-2026-08-25
description: "The 25 Aug engine session, four dashboard bugs from one screenshot, the brain wired in and the hole that opened, and the PWA on his phone"
metadata: 
  node_type: memory
  type: project
  originSessionId: 19b29a34-b90e-4522-a436-ab101179163d
  modified: 2026-08-25T03:22:45.839Z
---

**2026-08-25.** The full detail of the 25 August engine work, moved here out of `MEMORY.md`
when that index went over its size limit. Nothing here is new, it is the same record, kept whole.
The engine work described below was committed as `899f942` on branch `phase-1-logos-os`, and the
brain-side guard fix as `c86a6cd8` on the brain repo's main. Both were re-verified live before
being trusted: 13/13 provers and 11/11 on the guard test.

## LOGOS IS AN APP ON HIS PHONE

`https://desktop-gruls39.tail01147a.ts.net:8443/` then Add to Home Screen. Gold loop icon (his
pick of six, the one matching his own `0-9-9-0` maths), opens fullscreen with no address bar.
Manifest plus `apple-touch-icon` 180x180 plus `mobile-web-app-capable`, all verified live over
HTTPS. **Tailscale supplies the real certificate, which is the only thing iOS was refusing on,
so the microphone should now work on his phone for the first time.** LOGOI keeps the tailnet
root; the UI sits on `:8443` so neither displaces the other.

⚠️ Session cookie is `HttpOnly; SameSite=Strict` but NOT `Secure`. No exposure today (loopback
plus tailscale terminates TLS) but worth hardening.

## THE DASHBOARD COULD NOT RUN A SINGLE MISSION, and had never been able to

`/command` ran the model INLINE while every other station route already had a `?async=1` opt-in.
Diagnose takes 30 to 90 s on the local model; the Next proxy quits at **exactly 30.019 s**
(measured on a SHORT brief, so it was never about length). The page then said **"The engine
refused that"**, turning a proxy timeout into a decision the engine never made.

Now **202 in 0.06 s**, and **Klarnow's inline path is byte for byte unchanged at 96.8 s**
because they read the result off that same reply. **His mission was never lost, it finished
server side at 11:29; only the browser gave up.**

## KING'S ONE SCREENSHOT FOUND FOUR REAL BUGS

1. **Every RUNNING NOW card showed the same number.** The count was computed once from the newest
   mission and printed on all of them, sweeping in calls from other missions and from the prover
   suite. It said 8; his three missions had made **1 each**.
2. **The dashboard opened fifteen days in the past.** The feed started at cursor 0 and walked
   forward 100 rows every 8 s, so with 1,749 events that was **17 polls and over two minutes** of
   replaying 9 August while saying "the engine is idle" with missions live. Fixed with `?tail=N`;
   live state now appears in **4.4 s**.
3. **Five missions said WORKING for ever.** A killed process never writes `station.finished`, and
   every restart added more. The engine now closes them at boot as **`station.abandoned`, never
   `finished`**, because they did not finish and the log must not say they did.
4. **A crash calling itself a refusal.**

**New prover `prove-feed-truth.ts`, 10 checks, locks all of it. 13/13 provers pass.**

## THE BRAIN IS WIRED IN, AND WIRING IT OPENED A HOLE THAT IS NOW CLOSED

`src/lib/brain.ts` had **exactly one importer in the whole repo: its own prover.** The record
said the engine read his 923 files; no mission ever asked it a question.

Now wired into **diagnose, deliberately not build**, because `checkGrounding` compares the
builder's output against `mission.rawInput`, so notes in the builder would have the gate flag his
own notes as invented.

**Its first real run pulled `project_klarnow_os_deal.md` and
`project_logos_maths_and_agreement_2026-08-09.md` into a model prompt**, cap tables and deal
terms, both marked never leaves the laptop. Nothing left the machine, but only because the model
was local.

**`brain_retrieval` now imports `NEVER_LEAVES_PATHS` rather than copying it; a comparison of all
37 guarded entries found 16 more gaps**, including `LOGOS_PROTECTION_PACK`, `AGBIDI_SEED` and
`KING_OS_BREAKDOWN`. **Test `tests/unit/test_guarded_files_cannot_reach_a_model.py`, 11 checks,
fails the build if a guarded file is ever reachable again**, and asserts ordinary notes STILL
work, because a guard that blocks everything passes every security test.

## ⚠️ THE DIAGNOSIS IS NEVER GRADED

The grounding gate runs at BUILD, not diagnose. Measured the same night on thin briefs, the
engine invented *"Marketing teams at mid-sized SaaS companies"*, *"boosting conversion rates by
40%"* and *"a guaranteed refund if it doesn't work for you"*. Nothing flagged any of it.

**The saving grace: the gate grades the campaign against his RAW WORDS, not the diagnosis, so a
lie born at diagnose is caught at build.** The narrow real risk is the Clarity Brief he reads and
approves.

**The lesson is his own product's argument: the engine is exactly as grounded as the brief it is
given.** His long brief was accurate; the lazy one invented a company type, a statistic and a
legal promise.

## 🔁 THE PATTERN, AGAIN, FOUR MORE TIMES

A process holding configuration from before a change. LOGOI held a 12 hour old gate; the engine
ran 15 hour old code; LOGOI held the old retrieval guard; and the engine had to be restarted
twice more. **Always ask what the running process loaded and when, before questioning the value
on disk.**

## What the later 25 Aug session added

The work above was found sitting **uncommitted and unrecorded** when King asked a fresh session
to look at what a stopped session had been doing. It was re-verified rather than trusted
(`npx tsx scripts/run-provers.ts` run live, 13/13; `pytest` on the guard test, 11/11), then
committed. **Lesson worth keeping: a passing test does not mean committed code. Check git status
independently of what memory claims, even when the claim turns out to be accurate.**

**Cross references:** [[project-logos-engine-build-2026-08-23]] ·
[[project-logos-os-whole-picture-2026-08-24]] · [[project-logos-jarvis-mode]] ·
[[project-logoi-agent]]
