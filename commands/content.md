# /content · Social Content Autopilot

**Trigger:** User types `/content` OR says "create content", "write posts", "social media content for [topic]"
**Purpose:** Generate content for up to 9 social platforms from one brief, for King David's brand or for clients as a retainer service

---

## INPUT · What to gather

1. **Topic / angle**, what is the content about?
2. **Business type**, whose brand is this for?
3. **Goal**, awareness, leads, bookings, trust?
4. **Platforms**, which ones? (default: LinkedIn + Instagram + Twitter/X)
5. **Tone**, professional, casual, story-driven, educational?

If none given, ask: "What's the topic and who's it for?"

---

## PLATFORM FORMATS

| Platform | Format | Length | Style |
|----------|--------|--------|-------|
| LinkedIn | Long post | 150-300 words | Professional, story-driven |
| Instagram | Caption + hashtags | 50-100 words + 10 tags | Warm, visual, punchy |
| Twitter/X | Thread (5 tweets) | 280 chars each | Sharp, punchy, opinionated |
| Facebook | Post | 100-150 words | Friendly, community-focused |
| TikTok | Script (hook + body + CTA) | 30-60 seconds spoken | Energetic, direct |
| YouTube Shorts | Script | 45-60 seconds | Hook-driven, one idea |
| WhatsApp Status | Short + emoji | Under 50 words | Personal, warm |
| Threads | Short post | 50-100 words | Casual, conversational |
| Skool | Community post | 100-200 words | Educational, value-first |

---

## CONTENT FORMULA (all platforms)

```
HOOK, first line stops the scroll
BODY, the value / story / proof
CTA, one clear next step (not "follow me", something they DO)
```

**Model the proven winner (Rule 17):** hook in the FIRST line (win the first 3 seconds), one idea per piece, a CTA they DO. This is what actually travels, not a guess. **Stack:** `/content` (or `/content-engine` for the full pipeline) + `tools\goals.py` (aim at the goal) + this SOP + King's brand voice.

---

## TONE RULES (King David's brand)

- Faith-first, never pushy or manipulative
- Plain English, no jargon
- Honest social proof only, no exaggerated claims
- Help first, sell second
- Read brand_assets\brand_guidelines.md before generating client-facing content

---

## OUTPUT FORMAT

Generate each platform in a clearly labelled block:

```
── LINKEDIN ──────────────────────────────
[Post text]

── INSTAGRAM ─────────────────────────────
[Caption]
[Hashtags]

── TWITTER/X, THREAD ───────────────────
Tweet 1: [hook]
Tweet 2: [point]
Tweet 3: [point]
Tweet 4: [proof]
Tweet 5: [CTA]

[etc. for each requested platform]
```

---

## THE GATE · nothing ships until it passes (Rule #21)

Before any post leaves, verify:
1. **Brand + voice** against `brand_assets\brand_guidelines.md`.
2. **`/humanize`** (ALWAYS, for anything a human reads): strip the AI tells, **ZERO em-dashes or en-dashes**, sound human, sound like King. [[feedback-sound-human-not-ai]]
3. **Honest proof only** (Rule #20): no invented stats, testimonials, or claims.
4. **Client-facing? Run `/qa-master`, then King approves** before it goes out.
5. **Aim it at the goal** (`tools\goals.py`): awareness, leads, or bookings, then measure.

"It reads well" is not the bar. On-brand + human + true + aimed is.

---

## CLIENT SERVICE PRICING

When selling /content as a service:
- Starter: €150/month, 3 platforms, 8 posts/month
- Growth: €250/month, 6 platforms, 16 posts/month
- Full: €400/month, all 9 platforms, 30 posts/month

Pitch: "You give me one topic per week. I handle the rest across every platform."

---

## BATCH MODE

If user says "plan a month of content for [niche]":
1. Generate 4 weekly themes (one per week)
2. For each theme, produce content for requested platforms
3. Output as a content calendar with dates
