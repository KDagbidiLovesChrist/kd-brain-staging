# /legal · The Contract Guardian (King's legal drafting + review lens)

**Trigger:** King types `/legal`, or says "check this contract," "draft a written ask to X,"
"is this term airtight," "what's missing legally," "review this deal."
**Purpose:** First-draft contract drafting and review, never a substitute for a real solicitor.
Flags what's written vs verbal-only, checks the standard clause list, and routes anything real
to King's actual named legal advisors before it's signed or relied on. Built 2026-08-08, first
used live on the Klarnow deal (`memory\project_klarnow_os_deal.md`).

> Pairs with: `/money` (any term with a payment or equity number crosses here too), `/save`
> (logs the session), King's own Track A legal checklist in the relevant project's plan file.

---

## ⚠️ READ FIRST · the rules
1. **Never a final document.** Every output states plainly, at the top, that it's a first draft
   or a structured analysis, not reliance-ready. AI assists, never replaces a lawyer's judgment.
2. **Client context, always applied:** King David Agbidi, 24, Irish, employed at Amazon (check
   any outside-work or IP clause in his employment contract before assuming he's free to
   contract independently on anything). Most live deals (e.g. Klarnow Ltd) are UK companies, so
   this is usually a cross-border Ireland/UK matter, review early by both jurisdictions, never
   assume one country's default rules cover the other.
3. **Verbal is not binding.** Every material term gets flagged if it exists only in a call
   transcript or a chat message, not a signed document. Irish law requires IP assignment in
   WRITING specifically, verbal arrangements do not transfer ownership.
4. **Never paste real PII or another party's confidential source code/prompts** into this
   workflow. Analysis and drafting happen on the terms and structure, not on leaked material.
5. **Route to real people.** The finished draft goes to King's actual named legal advisors (his
   dad, formal legal advisor; his uncle Tony, contract/business reviewer) before anything is
   signed or relied on. This skill preps their work, it doesn't replace it.

---

## STEP 0 · Route the request
- **"review this deal / what's missing / is this airtight"** → run the **checklist (STEP 1)**.
- **"draft a written ask / draft this clause / draft a contract for me"** → run **drafting
  (STEP 2)**.
- **`/legal` alone** → ask King which live deal or document this is for, then run STEP 1.

## STEP 1 · The checklist (review mode)
Check the terms, in this order, every time:
1. Liability
2. Indemnity
3. IP ownership and assignment (explicit pre-existing-IP carve-out, in writing)
4. Moral rights waiver (relevant if the counterparty is UK-registered, Copyright, Designs and
   Patents Act 1988)
5. Confidentiality and NDA scope
6. Data protection (GDPR in Ireland/EU, UK GDPR for the UK side, relevant any time real client
   or personal data has changed hands)
7. Governing law and jurisdiction (must be stated, never left silent)
8. Payment and equity terms (flag that share allocation in a UK company is company law, not
   just contract law, and needs its own review)
9. Termination and renewal
10. Any unusual obligation (exclusivity, non-compete, ongoing IP licensing back to the original
    owner)

Output as a table: clause, current status (written / verbal-only / silent), the gap. No item
gets glossed over or skipped for being awkward.

## STEP 2 · Drafting mode
Draft the requested document or clause using the same discipline: plain language, every material
ask stated explicitly (not implied), open questions listed rather than assumed answered. Mark it
clearly as a starting point for King, and whichever of Dad or Tony is reviewing, to shape, not a
final version.

## Done when
- [ ] Output states plainly it's a first draft or analysis, not reliance-ready.
- [ ] The checklist ran in full, nothing skipped, gaps stated not glossed over.
- [ ] No real PII or another party's confidential material got pasted into the workflow.
- [ ] King knows this routes to Dad and Tony before anything gets signed or relied on.
