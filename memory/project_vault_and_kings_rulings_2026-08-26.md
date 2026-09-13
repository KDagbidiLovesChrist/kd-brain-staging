---
name: project-vault-and-kings-rulings-2026-08-26
description: "The local vault for King's own data including his medical records, built after he named his injury (Estate B, detail in _private), plus his rulings the same hour on faith in the product, the wolf, and monetisation through subtext"
metadata: 
  node_type: memory
  type: project
  originSessionId: 19b29a34-b90e-4522-a436-ab101179163d
  modified: 2026-08-30T01:11:52.769Z
---

# The vault, and the rulings that came with it · 26 August 2026

## What he disclosed, and it changes what the rules were for

**His brain injury was named that day.** The name is an Estate B term and lives in
`_private/estate_b/` only; his own words are held verbatim in `_private/estate_b/redacted_2026-08-30.md`.

The film he named is one woman's account of one specific type of that condition, an autoimmune
condition repeatedly read as psychiatric before the neurological cause was found. **Which type
his was is NOT known and must not be assumed from the film.** His records will say. His doctors
are the authority.

**⚠️ THE THING WORTH KNOWING.** The rules he wrote for how sessions must run are, almost line for
line, what cognitive rehabilitation after brain injury actually teaches, and he arrived at them
without reading any of it:

| his rule | what it is |
|---|---|
| **26** one stage at a time, never batch, wait for the yes | reducing working memory load |
| **18** show it visually, never only describe it | external representation |
| **15** one continuous brain, never make him re-explain | external memory doing the retrieval |
| **21** tested, approved, trusted, then live | error checking moved outside the person |

**The Master Brain is an external cognitive scaffold he built for himself, and it works well
enough that he runs a company on it.** He then said the medical use he wants is exactly this:
*"USE THIS DATA TO HELP FOR MEDICAL PURPOSES AS THIS HELPED KING WITH HIS BRAIN INJURY."*

The records describe what happened to him. **The system describes what he did about it**, and the
second is the more unusual artefact. Three months of it exists, dated and versioned in git.

## The vault, built the same hour

He said: *"I WANT TO INPUT ALL MY DATA IN MY LOCAL LLLLLM"* and *"HENCE WHY I WANT TO CONNECT
YOU TO MY PHONE."*

`tools/logoi_vault.py` plus `tools/prove_vault.py`. **36 attacks, all refused.** Four independent
doors, because independent probabilities multiply:

1. **on disk** `_private/` is gitignored, checked against real git rather than a string
2. **in retrieval** `_private/` is in `logoi_gate.NEVER_LEAVES_PATHS`
3. **in the lane** `assert_local()` raises BEFORE a file is opened, and the prover tests the
   ORDER by making the reader explode: a guard that refuses after reading has already lost
4. **the index itself** lives inside the vault, so a copy of everything is not sitting outside
   the doors, which is the classic way this kind of system leaks

**The phone door is live and proven end to end:** `POST /api/vault/drop` with an `X-Vault-Token`
header, over Tailscale, lands in `inbox/`, indexes on the same call, searchable immediately. A
wrong token and a missing token both give 403.

**⚠️ THE ONE REAL GAP: scans.** There is no OCR and no vision model on this machine, so a scanned
PDF or a photograph is registered and reported UNREAD rather than silently skipped. **Hospital
records are usually scans.** Two free local fixes, both named in `unread_report()`:
`ollama pull llama3.2-vision:11b` (about 8 GB, better for letterheads and tables) or Tesseract
plus pytesseract.

**Two real bugs found by using it rather than by reading it.** The token was never generated,
because `not tok or tok != _vault_token()` short circuits before the call. And a search for
the Estate B term beside "neurology" against a note containing both words returned NOTHING, because scoring
counted occurrences against a floor tuned for 97 long work documents. **That is the dangerous
direction for this lane: a false positive wastes a minute, a false negative tells a man his own
medical record is not in his own vault when it is.** Now scored on distinct term coverage.

**His rights, since he asked:** GDPR Article 15, Data Protection Act 2018. Subject Access Request
to the hospital, the HSE and his GP separately. Free, one month, extendable to three. One real
Irish caveat: health data can be withheld where disclosure is judged likely to cause serious
harm, and requests are sometimes routed through a health practitioner.

## HIS RULINGS, same hour, verbatim where it matters

**KING'S IDLE IS HIS BELIEF SYSTEM.** Supersedes the earlier provisional *"For now Idle will be
kingdavid me"*, and both are kept because he said the first one was provisional himself.

**FAITH IN THE PRODUCT, ruled and settled:**
- *"let him plaster Jesus christ as he sees fit"*
- *"if people have a problem they can walk away from his product"*
- *"but he wil be humble"*
- **"he will only have jesus in his personal"**

**That last line is the architecture.** Faith lives in the PERSONAL orchestrator. It is not
imposed through the business lane or the client product. A client buys an engine, not a sermon,
and he is free to be as openly Christian as he likes in his own layer. **The separation is his,
it is coherent, and it resolves the tension without either hiding the faith or preaching at
customers.**

**THE WOLF, his own words, kept whole:** *"be wary of the wolf. The big bad wolf huffs and puffs
and wears sheeps skin the lambs parents and then kills and eats the lamb simply because he was
greedy. take care of the innocent sheep king."* Recorded as given. Not interpreted here.

**MONETISATION THROUGH SUBTEXT:** *"inspiration and subtext and metaphorically analogies through
monetisation, i.e. Orthodox through an AI faceless YouTube channel. King will make a sick
pipeline for all skills he will use and have it on autopilot."* This connects directly to the
existing [[project_faceless_content_engine]], which is live and has video #1 finished.

## The three orchestrators, also named today

**PERSONAL** sees all of it and never leaves the machine. **LEGAL** nearly all, because it is
useless without the whole picture. **BUSINESS** is money, and **his own words: money is a fruit,
not the end.** So business is the narrowest of the three on purpose, and what it earns is fuel.

**Where the money is aimed, stated as a place rather than an amount for the first time:**
expanding his education, and the **Nigerian and Irish economies**. Both halves of where he is
from.

**What travels and what does not:** *"THE ENGINE IS THE HEART AND THE BRAIN IS THE KNOWLEDGE."*
Clients buy the heart. The brain stays his. If somebody wants the experience of him specifically,
he can connect his own LLLLLM to their engine with his brain intact, as a thing he does rather
than a thing they own. **A client's X can be higher than his**, and he takes a share of what the
method earns them, *"even if he gets 1 euro for every 10 euro"*, because **the point is to
educate**.

## Related

[[project_logos_commercial_model_2026-08-26]] · the pricing this revises: a 10 percent share is
now acceptable to him where the model assumed 2x on cost.
[[project_work_lane_and_boundaries_2026-08-26]] · the DCEO lane this vault is modelled on.
[[feedback_wisdom_and_knowledge_division]] · why the medical reading is offered and never asserted.
