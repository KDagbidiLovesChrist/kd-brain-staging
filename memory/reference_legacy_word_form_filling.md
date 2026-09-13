---
name: reference-legacy-word-form-filling
description: "How to fill old decorative Word forms (floating text boxes, no real fields, circle-the-answer style) without corrupting them."
metadata:
  node_type: memory
  type: reference
  originSessionId: 8e267a62-b714-4c5a-8d52-c4850b90bc5d
  modified: 2026-08-02T03:29:07.856Z
---

# Filling legacy Word forms (floating text boxes, "circle applicable", no real fields)

Learned 2026-08-01 filling [[project-whitney-housing-form]]. Applies any time a client/family form is an old
Word template with no fillable fields — free-text blanks are empty floating text boxes, and multi-choice
answers say "please circle which applies" with every option just sitting there as plain text.

**Method:** unpack -> edit XML -> pack (per the `docx` skill), never recreate the file from scratch if the
original's branding/logo must be kept — recreating is only a fallback when the original is truly too fragile
to touch (see below for when it isn't).

**Free-text fields:** each blank is an empty `<w:p>` inside a `<w:txbxContent>`. Find it by its unique
`w14:paraId`, add a `<w:r><w:t>...</w:t></w:r>` inside. Safe and reliable.

**"Circle the applicable answer" fields — do NOT use a floating oval shape.** A standalone `<v:oval>`
positioned `position:absolute; mso-position-horizontal-relative:text` does NOT reliably anchor to its
paragraph when nested inside floating-textbox > table > cell > paragraph (which is how these forms are
built). It rendered at the top-left corner of the page instead, no matter how the margins were tuned.
**Fix that works:** add a character border straight onto the run's own `<w:rPr>` —
`<w:bdr w:val="single" w:sz="18" w:space="2" w:color="FF0000"/>` plus `<w:b/>`. It boxes the exact word
because it's a property of that text, not a separately-positioned object, so it can never land in the wrong
place. It's a rectangle, not a circle, but reads unambiguously as "this one is selected."

**Gotcha:** the run to patch is the one immediately before the `<w:t>` you're targeting, i.e. inside
`<w:r><w:rPr>`. It is easy to instead patch the paragraph MARK's own `<w:pPr><w:rPr>` (which appears first,
higher up in the same `<w:p>` block) by accident — that changes nothing visible. Anchor the regex/edit on
`<w:r>\s*<w:rPr>` specifically, not a bare `<w:rPr>`.

**Gotcha:** some blank lines are ONE run of dots that visually reads as two separate blanks (Tenant blank +
Joint Tenant blank) separated by spaces, e.g. `".........          ........."`. To write on the first blank,
replace the WHOLE `<w:t>...</w:t>` content in one operation (trim N dots off the front, keep everything
after). A regex that greedily matches only the leading dot-run and stops will orphan the rest of the string
outside any tag and corrupt the XML (`Opening and ending tag mismatch` on pack/validate).

**Gotcha:** if the write-in text is longer than the original dots and the containing floating text box has a
fixed height, the extra line can get visually clipped at the box's bottom edge (data is still in the file,
just not visible). Find that specific `<v:shape ... style="...height:XXXpt...">` (search backward from the
section's header text for the nearest preceding `v:shape` tag) and bump its height by ~15-20pt.

**Rendering to check your work:** always render to PDF and actually look at it before calling it done — this
class of edit fails silently (wrong position, clipped text) in ways `pack.py`'s XML validation cannot catch.
On this Windows laptop LibreOffice isn't installed and the `docx` skill's `soffice.py` wrapper assumes a
Linux/macOS sandbox (crashes on `socket.AF_UNIX` here) — use Microsoft Word COM automation instead
(Microsoft 365 is installed): PowerShell `New-Object -ComObject Word.Application`, `Documents.Open`,
`SaveAs([ref]pdfPath, [ref]17)`, then `pdftoppm -jpeg` to get page images to actually view.

**Delivery gotcha:** a colored character border (`<w:bdr w:color="FF0000">`) can render as plain black in
some Word/viewer configurations even though it displayed red in the version rendered above. If the exact
colored appearance matters and the recipient isn't technical, send the PDF render, not the raw .docx — the
PDF freezes the look; the .docx's rendering is viewer-dependent.

Related: [[project-whitney-housing-form]] · docx skill (`skills\docx\`).
