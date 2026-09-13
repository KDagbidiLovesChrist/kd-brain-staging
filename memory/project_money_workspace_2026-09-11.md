---
name: project-money-workspace-2026-09-11
description: "King's money workspace (projects/money-workspace, hall M), built by Codex from Claude's briefs on 11 Sep: an honest Radar triage (nothing provably pays by 28 Sep; the warm route is Olly, then Aunty) and a paper Trading 101 sized at EUR 50, real money only after the 28th if he still chooses it."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T19:46:04.628Z
---

# The money workspace (11 Sep 2026)

**Why:** money is tight, about EUR 200 to the 28th ([[project-accountant-finances]]). His words, in
order: *"Need to flip money or do jobs like get trading agent .md workspace data hall"*, then *"Money
workspace triage and trading agent aswell but not you you continue KD storyboard"*, then *"The money
workspace can enter money hall for I have 50 euro to flip we can doing trading 101"*, then he chose
**"Paper now, real after 28th"**.

**How it is built:** Codex (door 3) from Claude's briefs in `_ops/briefs/` (money workspace, then
paper-trading stage 2); Claude reviews and commits. Folder `projects/money-workspace`, scaffolded by
`tools/new_project.py`. Backed up since 11 Sep through a narrow `.gitignore` allowance (allow
`projects/`, re-block it, allow back only this folder; the engine and every other project stay out;
key-shape scan found 0).

**The triage (`TRIAGE_2026-09-11.md`), all 92 pending Radar items checked:** NONE provably pays by
the 28th. The conditional shortlist is three ideas for The Buka (#19 a direct ordering page, #22 menu
photos, #96 an allergen chart), each only if Aunty agrees a NEW paid scope, paid by 27 Sep. The
practical order: clarify Olly's paid website build (the consultation), then one conversation with
Aunty; no unpaid work on the hope of a sale.

**Trading 101:**
- Stage 1 (`paper-trading/DISCOVERY.md`, `DESIGN.md`, `HONEST_RISK.md`) reviewed by Claude and sound:
  paper only, a keyless public price sample checked with one request, regulator figures (SEBI 93% of
  individual F&O traders lost money FY22 to FY24, checked at source by Claude; SEBI 7 in 10 intraday;
  FCA about 80% of CFD customers).
- Stage 2 briefed 20:30: a paper simulator with a fictional 50 and a flat fee, test first, one saved
  data snapshot, a report with the fee-versus-size table, and `REAL_MONEY_GUARDRAILS.md`.
- **Stage 2 DONE 20:44** (Codex, 90,809 tokens; then it hit its Plus limit, with the work already
  complete). Reviewed by Claude: 21 of 21 tests pass on Claude's own run; `simulate.py` makes no
  network call (only `fetch_snapshot.py`, run once); re-running it offline gave a byte-identical
  `REPORT.md` (sha256 3a3b6210...). **The result, fictional 50, a 1.00 flat fee:** the moving-average
  rule LOST 10.58% on the untouched evaluation period, against +4.15% for 25% buy-and-hold and
  +30.74% for 100% buy-and-hold; max drawdown 10.58%; 3 trades, 6.00 in fees. With zero costs it
  made +8.19%, so the fee is the difference. **The Trading 101 lesson** (checked by hand): a round
  trip needs a price rise of 16.1% to break even on a 12.50 position, 4.1% on 50, 0.5% on 500, 0.14%
  on 5,000. The report's verdict: "Keep this on paper; it does not justify real money."
  `REAL_MONEY_GUARDRAILS.md` quotes the faith filter and KILLED line 145 verbatim.
- **Real money:** only after the 28th, only if he still chooses it, under guardrails (a regulated EU
  broker, plain shares or index funds, EUR 50 hard limit never topped up, he places every trade, no
  agent ever holds an account, key or order route). It would reopen KILLED line 145 of the queue
  (*"Stock-/day-trading agent (2026-07-02), gambling-adjacent; parked behind the Orthodox screen +
  /money. Do not re-propose."*) and cross the queue's faith filter (*"no gambling, trading, ...
  lanes, ever"*). His call and his Orthodox screen, never an agent's. Claude does not edit the filter.

**Also fixed on the way:** the project template's three em dashes, which every new project inherited.
