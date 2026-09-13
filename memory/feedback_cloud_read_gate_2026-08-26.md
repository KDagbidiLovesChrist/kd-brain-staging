---
name: cloud-read-gate-2026-08-26
description: Claude opened an unlabelled Drive file that turned out to be Amazon Confidential, and the gate that now stops it
metadata:
  type: feedback
---

**2026-08-26. What happened.** King asked Claude to go through his data. In Google Drive there
was a file titled only **"Accepted terms"**, dated 16 Aug, that neither of them had read. Claude
judged it worth opening precisely because it was unknown. It was King's Amazon **"Global Data
Center Access Acknowledgement"**, signed 29 Nov 2024, marked **Amazon Confidential** on every
page, carrying an NDA that runs **five years from acceptance**. It was in a remote model's
context before anyone knew what it was.

**Nothing was written to disk.** The document was already properly recorded on 22 Aug in
`_private/amazon_dc_access_acknowledgement_read_2026-08-22.md`, so no new file was created and
none of the content was copied anywhere.

## WHY NOTHING CAUGHT IT, and this is the lesson

    LOGOI lane                          -> logoi_gate         guarded   OK
    ccr lane                            -> custom-router.js   guarded   OK
    Gmail / Drive / Notion, read by
    Claude DIRECTLY                     -> nothing at all     NO GATE

**The guards covered the doors King built and not the one he was handed.** Every lane he
designed had a gate on it. The connectors that arrived with the tool did not, because there was
no lane to put a gate on: Claude just reads them.

## THE FIX, built and proven the same hour

`logoi_gate.check_cloud_item(title, context)` decides whether Claude may **OPEN** something,
judged on the label alone, which is all that is known beforehand. That is a different question
from `check()`, which asks whether text may LEAVE. **Reading is the irreversible half.**

**The list is deliberately broader than `GUARDED_SUBJECTS`, and the economics are why.**
Refusing to send a question costs one local answer. Refusing to OPEN a file costs nothing at
all: Claude names the title and King says yes or no in one word. A false negative cannot be
undone. `"terms"` is in the list specifically because `"Accepted terms"` is what got through.

Also refused: anything with **no meaningful name**. "Untitled folder", "Document", "Scan".
Nothing known is not the same as known to be safe.

Prover: `tools/prove_cloud_gate.py`, **38 checks**.

## ⚠️ TWO BUGS THE TEST CAUGHT IN THE FIX ITSELF, same family

1. **`dceo` does not match `DCEO_Brain`.** The underscore is a WORD character, so there is
   no word boundary after "dceo". Folder names use underscores constantly (`DCEO_Brain`,
   `_private`, `term_sheet`), so every guarded folder would have walked through a guard that
   looked like it worked.
2. **Fixing that broke the hyphenated entries.** Splitting on `-` turned the text
   "non-disclosure" into "non disclosure", which no longer matched the list entry
   `"non-disclosure"`.

Both forms, raw and split, are now checked. **Either bug alone leaves a guard that passes its
own tests and protects nothing**, which is the same shape as `prove-sovereign` passing for
months with zero assertions.

## HOW TO APPLY

Before opening ANY cloud file, email or page for King, run `check_cloud_item` on its title.
If it refuses, tell him the title and the reason and let him decide. Do not open on your own
judgment, because the judgment has to be made before the information exists.

Related: [[project-lllm-logic-layer-2026-08-25]] (the gate and router work this extends) ·
[[feedback-verify-route-by-last-run]]
