---
name: project-cv-tailor
description: "CV Tailor LIVE, Joshua's Ryanair v4.2 signed off 2026-05-22. Interview-first principle now baked in as Step 0; two fabrications caught by direct interview."
metadata: 
  node_type: memory
  type: project
  originSessionId: 64e05a51-21d8-4515-b398-576edb173937
---

# CV Tailor · Brother's Engineering Job Search

## Status
**[LIVE, Joshua signed off v4.2 of the Ryanair pack on 2026-05-22, in his own words: "I'd send this."]** Major architectural upgrade landed: interview-first principle is now Step 0 of the SOP. Two fabricated "key achievement" stories were caught when Joshua was interviewed directly. System now produces verified-only content.

## Profile Fill State
**Verified, not just filled.** `applicants\brother\profile.md` and `master_cv.md` rebuilt from `joshua_interview.md` (22 questions across 10 sections, live chat with Joshua himself). All `[gap]`s closed except FYP supervisor name. Companion `joshua_voice.md` captures tone, preferences, honesty boundaries, don't-claim list.

## Joshua's Key Verified Facts (CV-relevant)
- **Name on CV:** Joshua Destiny Agbidi (full)
- **Location on CV:** Dublin, Ireland (Joshua's call, UK phone, OK with it)
- **Degree:** BEng (Hons) Aircraft Engineering with Pilot Studies, Salford, Sept 2023 → June 2026, expected 2:1
- **Age headline:** started at 17, **graduating at 19**, Joshua wants this to stand out
- **FYP:** Flow Visualisation, CFD post-processing in ParaView; supervisor provided dataset, Joshua did analysis only
- **Apple Specialist** (NOT "Sales Specialist"), 1 Aug 2025, 19 Jan 2026
- **Soul and Surf Front of House** (NOT "Bartender", Joshua flagged that as unprofessional), July 2023, July 2025
- **SolidWorks** (Year 1), **MATLAB** (Years 2, 3), **ParaView** (FYP). No Python.
- **Languages:** English only
- **Aviation regulatory study:** EASA Part M, CAMO, Part 145, MPD, MRB, MSG-3, core modules; NOT claimed as "expert" because Joshua himself said not currently fresh
- **Field trip:** Cranfield aviation facility at Blackpool (Salford-organised)
- **First Aid:** Red Cross Preliminary Sept 2022 (the one verified cert)
- **Voluntary:** SVP Coláiste Phádraig 2018 + community events Lucan/Manchester 2018, 2019

## Two Fabrications Caught and Permanently Scrubbed
1. **POS-outage story** at Apple, Joshua: "I don't even know what POS is." Never happened.
2. **Soul and Surf menu-item-off story**, Joshua: "That never happened." Never happened.

Both were on v1, v2, v3 of the Ryanair CV. Both came from King David's verbal context, not from Joshua. Now permanently in the don't-claim list across profile.md, master_cv.md, joshua_voice.md.

## v1 → v2 → v3 → v4.2 (Why It Took Four Tries)
- **v1** (2026-05-21): single-column reportlab PDF, BA-tailored prose. King David's verdict: "not good at all."
- **v2** (2026-05-22 morning): switched to Jake Amos two-column template, scrubbed AI-tells. Verdict: "fine but missing job-matching content."
- **v3** (2026-05-22 afternoon): aggressively job-keyword-matched. Verdict: "you exaggerated information that's not true." This triggered the rebuild.
- **v4 / v4.2** (2026-05-22 evening): interview Joshua directly → rebuild source files → render. Joshua signed off v4.2 on the second review iteration in his own words.

## Architecture Now In Place
- `applicants\brother\joshua_interview.md`, verbatim Q&A, source of truth
- `applicants\brother\joshua_voice.md`, distilled preferences, tone, don't-claim list
- `applicants\brother\profile.md`, verified-only, all gaps closed
- `applicants\brother\master_cv.md`, verified-only, structured
- `workflow\cv_tailor_sop.md` Step 0, **Applicant Interview Gate (NON-NEGOTIABLE)**. No CV gets produced before the applicant is interviewed.
- `tools\export_pdf.py`, HTML+CSS → PDF via Playwright (Jake Amos two-column visual)
- `tools\tailor_cv.py`, 1-page hard cap, template-aware, voice-file aware

## WAT Chain
- **W:** `workflow\`, recruiter_persona.md, humanizer_rules.md, cv_tailor_sop.md (with Step 0)
- **A:** Claude Opus 4.7 + per-agent personas (pending: specialist persona files)
- **T:** `tools\`, 4 agent scripts + master runner + Playwright PDF exporter
- **S:** `/cv-tailor`, global skill triggers the whole pipeline (but only after interview gate passes)

## Hard Rules (Permanent)
1. **Interview the applicant first.** Verbatim. Before any agent runs.
2. Sound human, not AI. Zero em-dashes in body text of CV or cover letter.
3. No auto-apply, no auto-send.
4. Honesty Boundary, only facts from interview / profile / master CV. Reframing yes, fabrication no. Stretch jobs flagged not faked.
5. CV = 1 page hard cap.

## Money Angle
Brother is Client Zero (signed off). Resaleable structure ready: add `applicants\[client_name]\` per the same pattern (interview → voice → profile → master_cv → tailored). Price target: €20, 50 per CV pack, €100/month per client. The interview is the moat, competitors don't do it.

## Outstanding For Future Sessions
- Joshua's FYP document (richer technical detail for FYP block when next job comes up)
- King David's CV structure spec (may override Jake Amos visual)
- FYP supervisor name (for referee list)
- Per-agent specialist personas (originally planned upgrade, still useful but de-prioritised after the interview-first rebuild)
- GPTZero AI-detector as a belt-and-braces final check

## Cross-references
- [[feedback-interview-applicant-first]], the interview-first principle this project proved out
- [[feedback-expert-judgment-exceed-brief]], push back when honesty is at stake
- [[feedback-sound-human-not-ai]], anti-AI tone rule; banned-words list in `CV Tailor\workflow\humanizer_rules.md`
