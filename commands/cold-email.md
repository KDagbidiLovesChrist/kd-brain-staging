# /cold-email · Outreach Generator

> ⛔ **STANDING KILL (King, 2026-07-03):** WhatsApp / SMS cold-send sprints and cold DMs are DEAD as King's hand-step, never propose them again. King tried them, no luck. Any outreach must be a DIFFERENT, warm motion (inbound content + products + warm circle) and only on King's explicit ask. The WhatsApp/SMS/cold templates below are kept ONLY as raw material to repurpose for WARM outreach. See `memory\feedback_no_cold_outreach_king_tried.md`.

**Trigger:** User types `/cold-email` OR says "write outreach", "cold message", "write a DM", "write an email to a [business type]"
**Purpose:** Generate personalised, honest cold outreach for any business type using the Solution-First Formula

---

## THE SOLUTION-FIRST FORMULA

Never lead with "I do AI" or "I build automations."
Lead with their problem. Always.

```
"I help [specific business type] [specific result].
I've [proof/method].
[Simple question to open conversation]."
```

---

## OUTREACH TEMPLATES BY CHANNEL

### WhatsApp / SMS (under 160 chars ideally)

```
Hi [Name], I help [business type] in [city] get more [leads/customers/bookings] 
without spending more on ads. I do this with [simple description].
Would it be worth a quick chat?
```

**Dublin Plumber example:**
```
Hi [Name], I help plumbers in Dublin stop losing leads to competitors.
I build a simple system that finds you 100 new contacts a month.
Worth a 5-minute chat?
```

---

### Email (short · under 100 words)

```
Subject: More [leads/customers/bookings] for [Business Name]?

Hi [Name],

I noticed [specific observation about their business, no website, no reviews, etc.].

I help [business type] in [city] [specific result].

I recently [proof, e.g. "got a Dublin plumber 50 new leads in one week"].

Would you be open to a quick call to see if it fits?

[Name]
```

---

### Instagram / LinkedIn DM

```
Hey [Name], love what you're doing with [business].

Quick question: are you finding it hard to [their likely pain point]?

I've been helping [business type] in [city] with this, got one client [result] recently.

Happy to show you how if you're interested.
```

---

## INPUT NEEDED

1. **Business type** (plumber, gym, clinic, etc.)
2. **City / location**
3. **Channel** (WhatsApp, email, DM, LinkedIn)
4. **Proof to use** (optional, any result from past work)
5. **Specific name** (optional)

If not provided, generate a template version with [placeholders].

---

## RULES

- Never mention "AI", "automation", "Claude", or any tech tool
- One problem, one result, one question, that's it
- Under 100 words for text/DM. Under 150 for email.
- No fake urgency. No manipulation. Honest offer only.
- End every message with ONE easy yes/no question

---

## BATCH MODE

If user says "write 5 cold emails for [business type]", generate 5 variations:
- Variation 1: Lead with pain
- Variation 2: Lead with proof
- Variation 3: Lead with question
- Variation 4: Lead with observation
- Variation 5: Lead with compliment + pivot

Output all 5 as a numbered list. User picks the best one.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
