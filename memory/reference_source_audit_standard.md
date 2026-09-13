---
name: reference-source-audit-standard
description: "The two-axis evidence standard (born 2026-07-18, King's push): a consensus claim must pass BOTH (1) audited source independence (authorship, lineage, incentive — not 'different websites') AND (2) traced measured results (every number followed to its origin, echo numbers discarded). Includes the QA-upgrade audit verdicts and the retired echo numbers. Apply in /research, /find-skills, any Rule #17 consensus call."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 8c95a916-4cdd-4546-b764-888f48c096e9
---

# The Source-Audit Standard (2026-07-18)

Born when King challenged "what does independent source actually mean to you?" during the /qa-master
upgrade scout. Two Workflow audits (23 agents, adversarial) proved his instinct right: the original
"3-5 source consensus" was inflated. This standard is now the bar for Rule #17 consensus claims.

## The two axes (BOTH required)
1. **Audited independence** — same author, same owner, copy-chains, aggregator reposts, and
   vendor-marketing funnels all collapse into ONE voice. Check authorship, commit dates (who was
   first), whether B credits/derives from A, and who profits. "Different website" ≠ different source.
2. **Traced results (King's axis)** — every headline number must trace to a real measurement
   (who measured, on what, n=?). If it only circulates in blogs quoting blogs → ECHO, treat as
   non-existent. Note when the measurer sells the thing measured. Hunt contrary evidence too.

## What the 2026-07-18 QA audit found (worked example)
| Pick | Claimed voices | Audited voices | Evidence tier |
|---|---|---|---|
| 5-step verification gate | 3 | 2 | Measured-once (adjacent: ReVeal +7.6pts Pass@1; gate itself never measured) |
| Test-must-fail-first | 4 | 2 | Measured-multiple (TDFlow 94.3% SWE-bench w/ failing-test oracle; TDD human studies MIXED) |
| Root-cause-before-fix | 4 | 2 | Measured-once (novices 60%→80% correctness, ~2.7x faster; no professional studies) |
| Fresh-context reviewer + FP filter | 5 | 4 | Measured-once (premise solid; the technique itself unmeasured) |
| Recon-then-action web testing | 2 | 1 (all Anthropic) | Measured-multiple (WebVoyager: look-before-act +17-19pts, ACL 2024) |

**The flip lesson:** the pick with the MOST voices had the weakest specific measurements, and the
pick that collapsed to ONE voice had the strongest neutral benchmark. The two axes catch different
failures — never run one without the other.

## Echo numbers permanently RETIRED (never cite again)
- "Evaluator-refiner ~20% better than self-refinement" — one blogger, unreferenced; his cited AWS
  page contains no percentage. (Misquote of Self-Refine's 20%-over-one-step, a different claim.)
- "~75% useful suggestion rate" (9-agent review) — the author's own words are "I'd peg": a guess.
- "r=0.89 LLM-judge alignment" as a universal fact — one narrow text-scoring result (Prometheus),
  authors scored their own judge.
- "Playwright 60% less flaky than Selenium" — no original study exists.

## Nuances the audit taught
- **Independent ADOPTIONS ≠ independent inventions.** Kent Beck invented red-green once (2002);
  modern sources adopting it is survival evidence, weaker than parallel discovery. Name the ancestor.
- **Self-checking without external grounding can make models WORSE** — verification must demand an
  executed command/test as proof, never self-assessment. (Also: naive "do TDD" prompting made agent
  regressions ~42% worse; the active ingredient is the failing-test-as-oracle, not the ceremony.)
- **Local incident data is top-tier evidence** — the two silent-failure incidents of 2026-07-16/17
  justify a "will it alert" QA class better than any blog could.

## Status
/qa-master v2 SHIPPED 2026-07-18 (King approved the session master plan; self-QA passed: qa_ref_check
+ brain_link_scan both exit 0; statically verified only — first dynamic proof comes with the next real
deliverable). v1 preserved in git history. Related:
[[feedback-consensus-everything-rule]] · [[feedback-multi-source-consensus-research]] ·
audit transcripts: session workflows `independence-audit` + `proven-results-audit`.
