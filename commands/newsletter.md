# /newsletter · AWS Weekly Digest Pipeline

Runs the full newsletter automation: fetch AWS news → Claude summarises → HTML email → send via Gmail.

## Steps to Execute

1. Navigate to the newsletter project folder:
   `cd "C:\Users\Dell\.claude\newsletter-demos"`

2. Check that `.env` has all required keys set:
   - `ANTHROPIC_API_KEY`
   - `GMAIL_ADDRESS`
   - `GMAIL_APP_PASSWORD`
   - `NEWSLETTER_RECIPIENT`
   If any are missing, tell King David which one and stop.

3. Install dependencies if not already installed:
   `pip install anthropic feedparser python-dotenv`

4. Run the master pipeline:
   `python tools\run_newsletter.py`

5. Report back to King David:
   - How many articles were fetched
   - What the newsletter subject line was
   - Who it was sent to
   - Confirm HTML preview is at `.tmp\newsletter.html`

## If Something Goes Wrong

| Error | Fix |
|---|---|
| `ANTHROPIC_API_KEY` invalid | Check `.env` · must be real key from console.anthropic.com |
| Gmail login failed | Use App Password, not regular password. Setup: myaccount.google.com → Security → App Passwords |
| `feedparser not found` | Run: `pip install feedparser` |
| `articles.json` not found | Run `python newsletter-demos\tools\fetch_rss.py` manually first (from brain root; drop the prefix if already `cd`'d into the project) |

## Money Angle
Change `RSS_FEEDS` in `newsletter-demos\tools\fetch_rss.py` to any RSS source → new newsletter product.
Sell to businesses: €50, 200/month per client. Finance, crypto, fitness, tech, legal, any niche.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
