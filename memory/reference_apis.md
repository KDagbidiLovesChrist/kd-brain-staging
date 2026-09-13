---
name: reference-apis
description: "Plain-English guide to APIs, what they are, how King David uses them, how to build one, and when to build vs use existing. Covers the restaurant kitchen analogy and FastAPI basics."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# APIs · Plain English Guide

## What Is an API?

**The restaurant analogy:**
You're sitting in a restaurant. You don't go into the kitchen to cook your food.
You talk to the waiter, the waiter goes to the kitchen, the kitchen cooks, the waiter
brings back the result.

That's an API.

- **You** = King David's code (or Claude)
- **The waiter** = the API
- **The kitchen** = the service doing the work (Anthropic, Firecrawl, Perplexity, etc.)
- **The menu** = the API documentation (what you can order)
- **The receipt** = the API key (proves you're allowed to order)

You never see the kitchen. You don't need to. You just know the menu and use the waiter.

---

## Part 1: USING APIs (What King David Already Does)

### APIs Currently In Use

| API | What It Does | Where Key Lives |
|-----|-------------|----------------|
| Anthropic API | Claude AI · summarising, writing, reasoning | .env: ANTHROPIC_API_KEY |
| Perplexity API | Deep web research on any topic | .env: PERPLEXITY_API_KEY |
| Firecrawl API | Web scraping, search, extract | .env: FIRECRAWL_API_KEY |
| Gmail SMTP | Send emails programmatically | .env: GMAIL_ADDRESS + GMAIL_APP_PASSWORD |
| Playwright | Browser automation (via MCP, no key needed) | Connected via settings.json |

### How API Calls Work (Plain English)

Every API call has 4 parts:
1. **The address (URL):** Where to send the request (like a website address but for code)
2. **The method:** What you want to do, GET (get data), POST (send data), DELETE (remove data)
3. **The headers:** Your credentials and settings (this is where the API key goes)
4. **The body:** The actual request (what you're asking for, in JSON format)

In Python, an API call looks like this:
```python
import requests

response = requests.post(
    "https://api.perplexity.ai/chat/completions",  # address
    headers={"Authorization": f"Bearer {api_key}"},  # credentials
    json={"model": "sonar", "messages": [{"role": "user", "content": "research topic"}]}  # body
)

data = response.json()  # get the response back as data
```

### API Keys · Handle With Care

An API key is like a password that gives access to a paid service. Rules:
1. **Never put an API key in code directly.** Always use .env files.
2. **Never commit .env to GitHub.** Always add .env to .gitignore.
3. **If a key is exposed:** Immediately revoke it in the service's dashboard and generate a new one.
4. **One key per service.** Each API (Anthropic, Perplexity, Firecrawl) has its own key.

---

## Part 2: BUILDING an API (When Clients Need a Webhook)

Sometimes a client needs to call YOUR automation from their system. That means you
need to expose an endpoint they can send data to. This is when you build an API.

**When you'd build one:**
- Client wants to trigger your lead scraper from their CRM
- Client wants their website contact form to send data to your processing system
- You want to sell access to your automation as a service (charge per use)

### FastAPI · The Simple Way to Build an API in Python

FastAPI is a Python library that makes building APIs easy. Install it:
```powershell
pip install fastapi uvicorn
```

Basic API example (a lead scraper endpoint):
```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

class ScraperRequest(BaseModel):
    trade: str          # e.g., "plumbers"
    city: str           # e.g., "Dublin"
    count: int = 50     # how many leads

@app.post("/scrape")
async def scrape_leads(request: ScraperRequest):
    # Call the scraper tool
    leads = run_scraper(request.trade, request.city, request.count)
    return {"leads": leads, "count": len(leads)}

# Run it:
# uvicorn main:app --reload
# Now clients can POST to http://localhost:8000/scrape
```

### API Security
Never expose an API without authentication:
```python
from fastapi import Security
from fastapi.security import APIKeyHeader

api_key_header = APIKeyHeader(name="X-API-Key")

@app.post("/scrape")
async def scrape_leads(request: ScraperRequest, api_key: str = Security(api_key_header)):
    if api_key != "your-secret-key":
        raise HTTPException(status_code=403, detail="Invalid API key")
    # proceed with scraping...
```

---

## Part 3: WHEN TO BUILD vs USE EXISTING

| Situation | What to Do |
|-----------|-----------|
| Need to research a topic | Use Perplexity API (already done) |
| Need to scrape a website | Use Firecrawl API (already done) |
| Need to send an email | Use Gmail SMTP (already done) |
| Need to generate content | Use Anthropic API (already done) |
| Client needs to trigger your automation | Build a FastAPI endpoint |
| Selling automation as a service | Build a FastAPI endpoint + authentication |
| Need to connect two systems | Usually an existing API handles this · search first |

**Rule:** Always search for an existing API before building one. 95% of the time, the
waiter already exists, you don't need to build a new restaurant.

---

## Part 4: API RATE LIMITS

Most APIs have limits on how many requests you can make. If you hit the limit, you get
a 429 error (Too Many Requests).

**Common rate limits:**
- Anthropic: varies by plan, Claude Max has higher limits
- Perplexity: varies by plan
- Firecrawl: varies by plan

**How to handle rate limits in code:**
```python
import time

def call_api_with_retry(payload, max_retries=3):
    for attempt in range(max_retries):
        response = requests.post(url, json=payload, headers=headers)
        if response.status_code == 429:
            wait_time = 2 ** attempt  # 1, 2, 4 seconds
            print(f"Rate limited. Waiting {wait_time}s...")
            time.sleep(wait_time)
            continue
        return response.json()
    raise Exception("Max retries exceeded")
```

---

## API QUICK REFERENCE

```
WHAT IS AN API:
  Waiter between your code and a service
  You send a request → service processes → response comes back

KEY RULES:
  Keys in .env → never in code, never in GitHub
  Check docs for rate limits before building
  GET = fetch data, POST = send data, DELETE = remove

KING DAVID'S CURRENT APIS:
  Anthropic  → Claude AI          → ANTHROPIC_API_KEY
  Perplexity → Web research       → PERPLEXITY_API_KEY
  Firecrawl  → Web scraping       → FIRECRAWL_API_KEY
  Gmail SMTP → Send emails        → GMAIL_ADDRESS + GMAIL_APP_PASSWORD

WHEN TO BUILD AN API:
  Only when a client/system needs to call your automation externally
  Use FastAPI + uvicorn → simple, fast, Python-native
```
