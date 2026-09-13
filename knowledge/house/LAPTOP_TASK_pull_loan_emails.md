# Laptop Task · Pull the Loan Emails (BACKUP route)

*Use this only if King would rather read the loan emails on the laptop instead of sending screenshots
into the chat. The MAIN route is simpler: King screenshots the loan emails in Yahoo and sends them
straight into a Claude chat, and Claude analyses them live.*

---

## Why this exists
The Yahoo inbox (`Kingdavidagbidi@yahoo.com`) cannot be read from a cloud / phone Claude session, and
it cannot be read by the brain's email tools either, because those tools read **Gmail**
(`kingagbidi@gmail.com`), not Yahoo. This file is the workaround for a laptop session.

## Steps

**Step 1 (King, in Yahoo):** forward every loan-related email to `kingagbidi@gmail.com`.
- Cover the run from **December 2025 to April 2026** plus the **2023** loan.
- Search Yahoo for: the lender names, "loan", "application", "declined", "approved",
  "thanks for applying", "your account".

**Step 2 (laptop Claude session):** read those forwarded emails with the existing tools:
- `tools/list_recent_mail.py` to list them, then `tools/read_recent_gmail.py` to read the bodies.
- (These need the Gmail token at `C:\Users\Dell\.claude\token.json`, which lives on the laptop.)

**Step 3 (laptop Claude):** build a loan-by-loan table and fold it into
`knowledge/house/CREDIT_HISTORY_EXPLANATION_2026-06-23.md`:

| Date | Lender | Amount | Outcome (approved/declined/withdrawn) | Stated reason |
|------|--------|--------|----------------------------------------|---------------|
|      |        |        |                                        |               |

The point of the table: prove the Dec 2025 to April 2026 run was **one need (the car), shopped to a few
lenders**, not many separate debts. Keep it strictly to what the emails actually say. Do not invent
amounts, dates, or reasons.
