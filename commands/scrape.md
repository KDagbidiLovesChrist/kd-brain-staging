# /scrape · Lead Gen Scraper Pipeline

Runs the full lead generation pipeline: scrape business directory → clean data → export CSV + Excel.

## Steps to Execute

1. Navigate to the scraper project folder:
   `cd "C:\Users\Dell\.claude\scrapers"`

2. Check that `.env` has `FIRECRAWL_API_KEY` set.
   If missing, tell King David and stop.

3. Ask King David (if not already specified):
   - What trade/niche? (e.g. plumbers, electricians, cleaners)
   - What city? (e.g. Dublin, Cork, London)

4. Run the scraper:
   `python tools\scrape_leads.py`

5. Run the Excel export:
   `python tools\export_excel.py`

6. Report back to King David:
   - How many leads were scraped
   - Where the CSV is saved (`.tmp\leads_*.csv`)
   - Where the Excel file is saved (`.tmp\leads_*.xlsx`)
   - Remind him: post to Fiverr if not done yet

## Fiverr Pricing
- 50 leads → €25
- 150 leads → €50

## If Something Goes Wrong

| Error | Fix |
|---|---|
| `FIRECRAWL_API_KEY` missing | Add to `.env` file |
| No results returned | Try a different search term or city |
| Excel export fails | Run `pip install openpyxl pandas` |

## Scaling
Change the search term and city to scrape ANY trade in ANY location.
Same script, infinite niches: plumbers, electricians, solicitors, gyms, restaurants.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
