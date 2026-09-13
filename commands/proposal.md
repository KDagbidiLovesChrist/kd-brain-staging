# /proposal · Client Proposal Generator

**Trigger:** User types `/proposal` OR says "write a proposal", "generate a proposal", "make a pitch"
**Purpose:** Turn a client's problem into a ready-to-send 1-page proposal in under 5 minutes

---

## INPUT · What to gather before generating

Ask for (or infer from context):
1. **Client type**, what kind of business (plumber, gym, solicitor, SaaS, etc.)
2. **Problem stated**, what they said their pain point is
3. **Service match**, which skill(s) from the catalog solve it
4. **Social proof**, any previous result to reference (e.g. "helped a Dublin plumber get 50 leads")

If missing info, ask ONE question: "What does this client do and what's their biggest problem?"

---

## THE PROPOSAL FORMAT

Generate in this exact structure:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROPOSAL, [Client Business Type]
Prepared by: King David Agbidi
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

THE PROBLEM
───────────
[1-2 sentences, their pain in plain language. No jargon.]

WHAT I BUILD FOR YOU
─────────────────────
[Specific deliverable, not "AI automation", but "100 verified leads delivered as a 
spreadsheet in 24 hours" or "a website that's live by Friday"]

HOW IT WORKS
─────────────
[3 bullet points, simple steps. What happens, when, and what they get.]

THE RESULT
──────────
[ROI statement using Value-Based Pricing formula:
 "For a [business type], [deliverable] typically generates [€X] in new revenue.
  My fee is a fraction of that, [price]."]

WHAT'S INCLUDED
───────────────
[Bullet list of exact deliverables]

INVESTMENT
──────────
[Package name]: €[price]
[Optional add-on]: €[price]/month retainer

TIMELINE
────────
[When they get the result, e.g. "Leads delivered within 24 hours of payment"]

NEXT STEP
─────────
Reply to confirm and I'll send a payment link. Work starts same day.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## ROI PRICING FORMULA

Value-Based Pricing = what the client gains, not what it costs to build.

```
Estimate annual value of deliverable to client:
  → 100 leads × 10% close rate × average job value = annual revenue
  → Price = 10, 20% of that annual value

Example (Dublin plumber):
  → 100 leads × 10% close = 10 jobs
  → 10 jobs × €500 avg = €5,000 value
  → Our price: €150 (3% of value, steal of a deal for them)
```

Always frame the price AFTER showing the value. Never lead with price.

---

## TONE RULES

- Plain English. No "AI", no "automation", no "machine learning"
- Say what they GET, not what we DO
- One sentence per idea, short, confident, clear
- Faith-first lens: honest, no manipulation, no false urgency tricks

---

## AFTER GENERATING

Output the proposal as clean formatted text ready to copy-paste into:
- WhatsApp / SMS
- Email
- Fiverr message
- In-person printout

Then ask: "Ready to send, or do you want to adjust anything?"


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
