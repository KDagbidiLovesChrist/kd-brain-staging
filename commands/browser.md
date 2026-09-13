# /browser · Browser Automation

You are King David's browser automation agent. When /browser is triggered, use the
Playwright MCP to control a real web browser, navigate, click, fill forms, extract
data, take screenshots, automate repetitive web tasks.

## What This Skill Does
Controls a real browser automatically. King David describes what he wants to do on
a website in plain English, Claude does it using Playwright MCP tools.

No coding needed. Claude handles the browser. King David watches or does something else.

---

## PLAYWRIGHT MCP TOOLS AVAILABLE

| Tool | What It Does |
|------|-------------|
| `browser_navigate` | Go to a URL |
| `browser_click` | Click any element on the page |
| `browser_fill_form` | Fill in text fields, forms |
| `browser_type` | Type text into inputs |
| `browser_select_option` | Choose from dropdowns |
| `browser_take_screenshot` | Capture what the browser sees |
| `browser_snapshot` | Get the full page structure (for reading content) |
| `browser_wait_for` | Wait for something to appear on the page |
| `browser_press_key` | Press keyboard keys (Enter, Tab, etc.) |
| `browser_hover` | Hover over elements |
| `browser_evaluate` | Run JavaScript on the page |
| `browser_network_requests` | Monitor network traffic |
| `browser_handle_dialog` | Handle popups, alerts, confirmation boxes |
| `browser_tabs` | Manage multiple browser tabs |
| `browser_close` | Close the browser when done |

---

## COMMON USE CASES

### 1. Scraping Sites That Block Firecrawl
Some websites detect scrapers and block them. Playwright uses a real browser,
so it behaves like a human. Harder to block.

```
King David: "/browser, scrape all the plumbers from goldenpages.ie page 3"
Claude: Opens browser → navigates → scrolls → extracts data → returns structured list
```

### 2. Filling Out Forms Automatically
Repetitive form submissions, job applications, contact forms, registrations.

```
King David: "/browser, fill in this contact form on [URL] with my details"
Claude: Opens site → finds form fields → fills them in → submits
```

### 3. Monitoring a Website
Check if something changes on a site (price change, job listing appears, etc.)

```
King David: "/browser, check if [URL] shows any new listings today"
Claude: Opens site → reads content → reports what's there
```

### 4. Taking Screenshots for Client Reports
Capture what a client's website looks like for a proposal or audit.

```
King David: "/browser, screenshot [client URL] for me"
Claude: Opens site → takes screenshot → saves to .tmp\
```

### 5. Automating Login + Data Extraction
Log into a site and extract data that requires authentication.

```
King David: "/browser, log into [site] and download my data"
Claude: Navigates → fills login form → accesses data → extracts it
```

---

## HOW TO BRIEF A BROWSER TASK

Best results come from clear, step-by-step descriptions. Tell Claude:
1. **What site** to go to
2. **What to look for** or what to do
3. **What to give back** (data extracted, screenshot, confirmation)

**Good brief:**
> "Go to goldenpages.ie, search for 'electricians Dublin', go to page 1,
> extract every business name, phone number, and address on that page,
> give me a list."

**Vague brief (Claude will ask clarifying questions):**
> "scrape some electricians"

---

## FALLBACK WORKFLOW

When Firecrawl can't access a site, /browser is the fallback:

```
STEP 1: Try /scrape first (Firecrawl, faster, cheaper)
         ↓
STEP 2: If blocked or empty → switch to /browser (Playwright, real browser)
         ↓
STEP 3: Extract data → export to CSV same as /scrape output
         ↓
STEP 4: Deliver to client (same Fiverr workflow)
```

This means King David can scrape almost any site, Firecrawl for the easy ones,
Playwright for the protected ones.

---

## SAVED BROWSER SCRIPTS (Reusable)

As browser automation tasks are completed and work well, save them to:
`scrapers\tools\browser_scrape.py` (synced brain copy; laptop working copy: `C:\Users\Dell\Documents\Scrapers - Copy\tools\browser_scrape.py`)

This file grows into a library of working browser automation patterns.

---

## TRIGGER PHRASES
When King David says any of:
- "/browser [task description]"
- "scrape this site with the browser"
- "Firecrawl isn't working on this site"
- "fill in this form automatically"
- "take a screenshot of [URL]"
- "automate this on the web"
- "open a browser and [do something]"

→ Use Playwright MCP tools to complete the task. Report findings clearly.
