---
name: interview-applicant-first
description: "For any CV / personal-document work, interview the actual person (verbatim) before generating content. Verbal context from third parties is a fabrication risk, interview-first is the moat."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: f62b8a91-22d3-4797-a4c8-c66b827c538f
---

For any CV, cover letter, or personal-narrative content, interview the actual person first, verbatim, before producing anything. Third-party verbal context (even from a close family member who knows them well) leads to padded content with fabricated specifics that the person themselves can't defend at interview.

**Why:** In May 2026, the CV Tailor project went through 3 versions of Joshua's Ryanair CV based on King David's verbal context about his brother. v1 was rejected ("not good at all"). v2 was rejected ("missing job-matching content"). v3 was rejected ("you exaggerated information that's not true"). When Joshua was interviewed directly in v4 prep, two specific "key achievement" stories on every prior version (the Apple POS-outage story and the Soul and Surf menu-item-off story) were confirmed by Joshua to **never have happened**. Both were fabrications stemming from third-party retelling. v4 was signed off by Joshua himself on the second review iteration.

**How to apply:**
- Any time the goal is "represent this person on paper" (CV, cover letter, bio, profile, intro), insist on interviewing the person directly before generating content. Live chat, async questionnaire, or scheduled session, modality flexible. Verbatim is non-negotiable.
- Capture answers in a dedicated `*_interview.md` file. Distill preferences and tone into a `*_voice.md` file. These two files become the source of truth.
- When a user offers "I'll just tell you about them", push back kindly: that produces v3-style fabrications. Schedule the direct interview.
- The interview also catches "what NOT to claim", equally important as what to claim.
- Step 0 of the CV Tailor SOP (`c:\Users\Dell\Documents\CV Tailor\workflow\cv_tailor_sop.md`) now enforces this as a hard gate. Future paying clients get the same protection.

Related: [[expert-judgment-exceed-brief]] (don't just execute instructions, push back when honesty is at stake), [[sound-human-not-ai]] (no AI tells in CV-style output), [[project-cv-tailor]] (project status).
