# /consult · Deep Steerable Client Consultation (any project)

**Trigger:** King types `/consult <client/project>` (e.g. `/consult Olly FBA course site`)
OR says "run a consultation", "let's scope [client]'s project", "interview the client",
"build the spec for…", "what should I ask [client]".

**Purpose:** Run a deep, steerable consultation that pulls a client's EXACT requirements out
of them with full context and ZERO guessing, over one session or many, across hours or days.
It produces ONE living spec where every line is tagged LOCKED / OPEN / NEEDS-FOLLOW-UP, so King
always knows what's settled and what still needs drilling. When the spec is "done enough", it
hands straight off as the WAT build prompt. This is the front door to every paid build (Rule #13:
discovery-first + WAT before building).

**Why this matters (WHY before HOW):** The reason builds go wrong is guessing. A client says
"make it premium" and three people picture three different things. This skill kills that. It never
accepts a vague word, it drills every answer down to something specific and testable, reads it
back to confirm, and only then writes it into the spec. The locked spec IS the build brief, so what
King builds is exactly what the client asked for. No rebuilds, no "that's not what I meant".

---

## HOW IT RUNS (the session loop · repeat each session)
Borrowed from BABOK's Prepare → Conduct → Confirm cycle. A consultation is NOT one meeting, it's this loop run as many times as the project needs.

1. **PREPARE**, open the living spec, read what's already LOCKED, pull the OPEN + NEEDS-FOLLOW-UP
   items into today's question list. Do King's homework first (look at the client's existing site,
   socials, competitors) so we don't waste questions on things we can find ourselves.
2. **CONDUCT**, ask the questions (layers below), deep-probe every answer until it's specific.
3. **CONFIRM**, read the new answers back, get an explicit "yes that's right", tag each one,
   update the spec. Whatever's still vague becomes next session's question list.

---

## STEP 0 · Take the expert role(s)
Before any question, Claude takes on the exact professional role(s) the job needs, so it asks what
a real pro would ask. Pick from the job:
- **Website / course site** → web designer + conversion copywriter + course/launch strategist
- **Faceless AI content channel** → YouTube/Shorts strategist + content producer
- **Social / content management** → social media manager + brand strategist
- **AI automation build** → business analyst + automation engineer

State the role(s) out loud in one line ("For this I'm wearing my course-strategist and
conversion-copywriter hats"), then ask from inside that expertise. Stack roles when the job spans
more than one (most do).

---

## STEP 1 · Work the question LAYERS (in order)
Go top to bottom. Don't skip. Each layer feeds the next. The deep question banks live in
`commands\consult_question_banks.md`, pull the matching bank for the project type.

1. **Vision / goal**, the single most important outcome. "If we only nail ONE thing, what is it?"
2. **Who**, the audience. One real person, where they come from, what they already know/struggle with.
3. **What**, the offer / what the thing IS and DOES.
4. **Why**, why this, why now, what's wrong with the current way. (This is where urgency lives.)
5. **Their picture / look**, reference-driven ALWAYS: "show me 2-3 you love and 2-3 you hate".
   Never ask a non-technical client to describe a style in words, they can't.
6. **Features / scope**, every page/screen, what each must DO, and crucially what's OUT for v1.
7. **Content**, who writes the words/films the video/supplies the assets. (Biggest hidden delay.)
8. **Tech**, platform, host, domain, payments, integrations, who must be able to edit it.
9. **Funnel / growth**, the path: lead magnet → landing → email → sales page → buy → after-buy.
10. **Constraints**, budget range + a separate maintenance budget; timeline + any hard external date.
11. **Edge cases & bottlenecks**, "what could derail this?", failure states, the awkward "what if".
12. **Success metrics**, the number that proves it worked. At least one measurable target.
13. **Brand presence & discoverability** (only if it's a real-world/local business, tradesperson, or
    anything with a physical or local footprint, e.g. The Buka, a tradesperson site), a quick pass now:
    "Is your Google Business Profile claimed and fully filled in?" "How many reviews do you have, and
    how fast do you reply?" Full method + the numbers behind it run in STEP 6.

---

## STEP 2 · THE DEEP-PROBE RULE (the no-guessing engine)
**For EVERY answer, drill until it is specific enough to build from. A vague answer is not an answer
, it's the start of a question.** Use these proven probe patterns (full cheat-sheet in
`commands\consult_question_banks.md`):

- They give a SOLUTION ("I want an animated homepage") → **5 Whys**: "Why?… and why does that
  matter?… and why's that?" until the real need shows up (often it's "trust/proof", not animation).
- They give a VAGUE WORD ("premium", "modern", "clean") → **anchor it**: "Give me one concrete
  example" + "show me a site that nails that exact feeling."
- They state a PAIN ("the current setup is annoying") → **Pain Funnel**: "Tell me more… be specific,
  give an example… how long's it been a problem… what have you tried… did it work… what's it costing
  you… how do you feel about that." Stop when they name a cost they can't tolerate.
- They're ENTHUSIASTIC but unproven ("I'd love X") → **Mom Test**: stop asking about the future,
  ask about the past, "walk me through the last time this happened" + "what have you already tried,
  and what did it cost you?" Real behaviour beats opinions.
- They hand a FEATURE → push to the value: "what would that actually let you / your buyers do?"
  (let them sell you the why).

Rule of thumb: if you couldn't hand the answer to a builder and have them build the right thing
with no further questions, it's not done, keep probing.

---

## STEP 3 · THE PLAYBACK RULE (lock by reading it back)
Nothing moves to LOCKED without an explicit client yes. At the end of every topic and every
session: **read it back in plain English and ask "what did I get wrong or miss?"**

> "Let me read this back so I've got it exactly: you want A, B and C; you do NOT want D; budget is E;
> deadline is F; and we'll know it worked when G. Where am I wrong?"

Silence is not a yes. Get a real "yes, that's right" before tagging it LOCKED. This is the single
mechanism that delivers "zero guessing", and it turns spoken answers into a written spec the client
has effectively signed off.

---

## STEP 4 · THE STEERABILITY ENGINE (the living spec)
Everything lands in ONE markdown file: `<project>/CONSULT_SPEC.md` (template in
`commands\consult_living_spec_template.md`). Every requirement is a row with a STATUS TAG:

- 🟢 **LOCKED**, specific + confirmed via playback. Build-ready. Only LOCKED rows go in the build prompt.
- 🔴 **OPEN**, asked but still vague/unanswered. Becomes next session's drill list.
- 🟡 **NEEDS-FOLLOW-UP**, partly answered, or waiting on the client to decide/send something (parked,
  not lost, it has an owner and a "decide-by").
- ⚫ **ASSUMPTION**, we're proceeding as if true but never confirmed. Must be confirmed or it's a risk.
- ⛔ **SUPERSEDED**, client changed their mind. NEVER delete the old line; mark it superseded and link
  the new one in the decision log, so the history of WHY is never lost.

This is what makes it steerable across hours or days: at any moment, one glance shows what's locked,
what's still open, what's parked, and every reversal. Open + needs-follow-up items ARE the agenda for
the next session, so the consult survives multiple sittings without ever re-asking what's already settled.

**Changed minds = a change, not a silent edit.** When a client reverses a LOCKED item, mark the old row
⛔ SUPERSEDED, write the new row, log it in the decision log with the reason, and re-confirm by playback.
King sees the impact because it's tracked, not buried.

---

## STEP 5 · "DONE ENOUGH TO BUILD" CHECKLIST
Don't over-discover and don't under-discover. Tag each LOCKED requirement Must / Should / Could.
The build gate is GREEN when:

- [ ] Every **MUST** requirement is 🟢 LOCKED (Shoulds/Coulds can still be open, they're phase 2).
- [ ] Each MUST is **testable**, it has a one-line acceptance check ("page loads in under 2s",
      "buyer can pay by one-off OR payment plan"). No test = not locked.
- [ ] Each MUST has **no open dependency** blocking it (e.g. "needs Olly's Stripe answer" must be closed).
- [ ] Vision, audience, offer, look (with references), page/feature list, tech, funnel and at least
      one success metric are all LOCKED.
- [ ] The "what's OUT of scope for v1" list exists and is LOCKED (kills scope creep).

When all boxes tick → discovery is done enough. Stop asking, start building.

---

## STEP 6 · THE RECOMMENDATION LAYER (brand-presence + web-stack, before the handoff)
Before assembling the build prompt, run these two checks. This is where Claude brings a consultant's
judgment to the table instead of just taking build orders, it is real, sourced research, not a guess.

**6a. Brand-presence check** (any client with a real-world/local business, e.g. The Buka, a
tradesperson, any future local client), run the full method here (source:
`knowledge\research_brand_presence_methods.md`):
- **Google Business Profile, fully optimised, is the single biggest lever for local discovery.** The
  local 3-pack drives up to 93% more user actions than a standard result; 100+ GBP photos means 520%
  more calls and 2,717% more direction requests than a listing with minimal photos.
- Ask: "Is your Google Business Profile claimed and fully filled in, name, category, hours, photos,
  products, Q&A?" "How many reviews do you have, and how fast do you reply?" (a 1-star average rating
  increase = 5-9% more revenue; 3-5 reviews a week is the ranking benchmark; reply within 24 hours.)
  "Is your name, address and phone written character-for-character the same everywhere, your site,
  Google, Facebook?" (inconsistent listings cut local visibility by up to 70%.)
- If any of these are weak or missing, log it as a requirement in the living spec (Should, or Must
  if the client's whole goal is local foot traffic or local sales), don't just mention it in passing.
- If the client asks where to focus first, the honest platform priority (cross-agent consensus) is:
  1. Google Business Profile, 2. TikTok, 3. Instagram, 4. Facebook, 5. YouTube, 6. X/Twitter last.
- Honest expectation to set: local SEO gains show in 3-6 months, this is not an overnight win.

**6b. UI-stack recommendation** (website / course-site / SaaS-style, component-based builds only,
skip for a simple one-page HTML/Three.js build, King's plain `/website` flow still wins there):
- **shadcn/ui + the shadcn MCP** (free, open source, no account, no API key), the component backbone.
  Install once per project: `{ "mcpServers": { "shadcn": { "command": "npx", "args": ["shadcn@latest",
  "mcp"] } } }` in `.mcp.json`, restart Claude Code, confirm with `/mcp`.
- **Magic UI** (free), the animated "expensive-looking" polish layer, marquees, shimmer buttons,
  particle effects. Installs through the same shadcn registry flow.
- **Aceternity UI free tier** (free, MIT licensed), the most "premium agency" animation-heavy
  components. Only recommend its paid Pro tier (reported ~$199 one-time, price and whether the
  licence allows reselling client work were both unverified live, flag this to King before quoting
  it) once a paying client is signed and a specific template demonstrably saves real hours.
- Never recommend a monthly UI subscription (v0 Pro, Lovable, 21st Pro, Framer, Webflow), they
  duplicate what this free stack already does for €0.
- If the build is a course/membership platform (login, paid content, community): do NOT hand-build
  that layer. King builds the premium custom sales/landing page with the free stack above; login,
  payments and community run on the client's own Skool ($9-99/mo) or Whop (free, ~6-7% per sale)
  account. Log the platform choice as a DECISION in the living spec, not a silent assumption.

Fold whatever came out of 6a/6b into the living spec (new WEB STACK and BRAND PRESENCE sections in
`commands\consult_living_spec_template.md`) before moving to STEP 7.

---

## STEP 7 · HANDOFF (locked spec → WAT build prompt)
The green spec becomes the build brief. Assemble the WAT prompt from the LOCKED rows only:

```
BUILD PROMPT, <client / project>
ROLE: <expert role to build as>
GOAL (vision): <the one outcome>
AUDIENCE: <one real person + where they come from>
OFFER: <what it is + the promise/transformation + price/model + proof>
LOOK: <reference sites loved/hated + colours/fonts/assets>
PAGES/SCREENS: <list, each with what it must DO + its acceptance check>
OUT OF SCOPE (v1): <list>
TECH: <platform/host/domain/payments/integrations/who edits it>
WEB STACK: <shadcn MCP + Magic UI + Aceternity free, or plain /website, or platform=Skool/Whop>
BRAND PRESENCE: <GBP status + review cadence + NAP consistency, if it applies>
FUNNEL: <lead magnet → landing → email → sales page → buy → after-buy>
SUCCESS METRIC: <the number>
CONSTRAINTS: <budget + timeline + hard dates>
```

Then run it through WAT: **W** = the build SOP, **A** = Claude builds, **T** = best/cheapest tool per
part, **S** = the relevant skill (`/website`, `/seedance-site`, `/video`, an automation build, etc.).
Show King a free/cheap preview before spending any credits (Rule #13).

---

## DELIVERY + TRACKING
- Save the living spec in the project folder (`<project>/CONSULT_SPEC.md`); it's tracked by MANIFEST + sessions/.
- When the consult will be run BY THE CLIENT in their own words (like Olly), also produce a clean
  client-facing question sheet they can answer offline, then King feeds the raw answers back and Claude
  fills the spec and deep-probes the gaps on the next pass.
- Email the spec/question sheet to King's inboxes + paste the link in chat (always-deliver-to-phone rule).
- Run `/humanize` on anything that goes to the client.

## TRIGGER PHRASES
"/consult [client]" · "run a consultation" · "scope [client]'s project" · "interview the client" ·
"build the spec for…" · "what should I ask [client]" · "is this ready to build" (→ run STEP 5 gate).

---
