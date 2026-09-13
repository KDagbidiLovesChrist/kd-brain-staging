# One price table, not three · 9 September 2026, evening

Satellite of [project_engine_and_hearts_2026-09-09.md](project_engine_and_hearts_2026-09-09.md),
which is already at 776 lines and past the 500-line rule. This is the price half only.

---

## What King asked, and the honest answer

**His question:** *"open ai deepseek and openrluter will be used thru cloud subs and wdym engine
has no codex . does it have clayde?"*

A models list is free, so it proves a key is **valid** and nothing more. OpenAI's key looked
healthy that afternoon by exactly that test and had **no credit**. So he said *"let know for
certain rather than assume"*, and one real call settled it.

```
ONE REAL CALL TO CLAUDE, 20 tokens, about USD 0.0004

  ANSWERED in 1526 ms
  model      : claude-sonnet-4-5-20250929
  said       : {"ok":true}
  tokens     : 16 in, 8 out
  cost       : USD 0.000168

  VERDICT: the key is FUNDED. The engine's Claude lane is alive.
```

**Valid and funded are two different questions.** Only a real message answers the second one.

---

## The bug the answer uncovered, which was worth more than the answer

Recording that call on the ledger made the meter print **USD 0.0000** for a call the engine had
just priced at **USD 0.000168**. Same sixteen input and eight output tokens, two different answers.

Neither side was broken. There were **three price tables**:

| file | keyed by | had claude-sonnet-4-5 |
|---|---|---|
| `tools/logos_lanes.py` `PRICE_PER_1M_USD` | tier (fable, opus) | not applicable |
| `tools/spend_meter.py` `PRICE_PER_1M_USD` | model | **no** |
| engine `src/lib/spend-gate.ts` `PRICE_PER_1M` | model | yes |

Nothing had ever compared them. **This is exactly the drift the lanes export was built to end,
and prices had simply never been added to it.**

### The fix, in two halves, because the first half was not enough

**Half one:** `tools/logos_lanes.py` grew `MODEL_PRICE_PER_1M_USD` beside its tier table, exported
as `model_prices_per_1m_usd` in `_ops/logos_lanes.json`. The meter and the engine's gate both read
it; each keeps its own dict only as a fallback for a process with no export, since several provers
boot without `LOGOS_LANES_JSON` and a gate that cannot price refuses every paid call.

**Half two, the part that was nearly missed:** adding the price changed nothing about the Claude
row. It had been **written** with its zero baked in, and the summary read `est_usd` straight out of
the row. The understatement would have been permanent. So the meter now **reprices a row flagged
`priced: false`** from its own recorded tokens. Those counts are real, taken from the vendor's
usage block, so it is arithmetic on measured data, not a guess. A row priced when written keeps its
figure, so settled history is never rewritten; a tier still absent stays flagged and is now
**named** in the output rather than being an anonymous count.

**Before and after, same ledger:**

```
    anthropic   1 calls   16 in    8 out  USD  0.0000      <- before
    anthropic   1 calls   16 in    8 out  USD  0.0002      <- after
    live-check  USD 0.0001  ->  USD 0.0003
    3 unpriced  ->  1 repriced, 2 still unpriced and NAMED:
                    nvidia/nemotron-3-nano-omni-30b-a3b-reasoning, z-ai/glm-5.3-flash
```

Those two stay flagged on purpose. **A guessed price is silent; a missing one is reported.**

---

## The lesson, which is the reusable part

**A rule enforced in three places is three rules.** The lanes export exists so Python and the
engine cannot disagree, and it worked for routing and ceilings precisely because something reads
it. Prices were left out, so prices drifted. Anything that must be true on both sides belongs in
that export, and **something has to compare them or the agreement decays at the next edit.**

Two provers now do the comparing, and both were added in the same commits as the fix:

- **`scripts/prove-price-parity.ts`, 12 of 12.** It reads the gate's fallback table **out of its
  own source text** rather than importing it, so the gate cannot pass by agreeing with itself. It
  checks the two tables match on every model, that nothing the engine prices is missing from the
  export, that the exact 9 Sep call prices to 0.000168, that a **doctored** export overrides the
  local copy (proving shared really wins rather than merely backstops), that an unknown model still
  returns `priced=false` so the gate can refuse instead of guessing, and that the fallback alone
  still prices with no export at all. The runner globs `prove-*.ts`, so it is in the suite with no
  list to maintain.
- **`tests/unit/test_spend_meter.py`, 11 of 11**, added to `tests/real_coverage_gate.sh` in the
  same commit per the standing rule. Gate green at **67.49%** against a floor of 50.

**Commits:** `e952ec83` (the one table) · `689e5b7a` (the meter tests; note the repricing code
itself landed in the `d606f1db` auto-sync, so the reason is recorded here rather than in that
message) · engine `7fd9aae` (the gate reads shared, plus the parity prover).

**Engine suite 30 of 34, unchanged.** The four failures were verified to fail **identically at
HEAD with both changed files reverted**, so none is mine: two need `LOGOS_LANES_JSON` or
`LOGOS_LOCAL` set, two need a seeded tenant.

---

## Flagged for King, then ruled by him the same evening

The full Python gate run surfaced **7 failures, all pre-existing** (proven by stashing and
re-running). Six are live-machine state. **The seventh is a real guard doing its job:**

`tests/unit/test_sync_claude_to_drive.py::test_no_method_file_is_reachable_on_any_real_route`
reports `memory/project_engine_and_hearts_2026-09-09.md` as carrying **4 method markers** and
reachable **via git and Drive**.

Every hit is either **a guarded filename** in an inventory of which files were rescued, or the one
line that lists what a certain prompt *does not* contain. No method content is reproduced anywhere
in it. That is the case `ALLOWLIST` exists for.

*(This satellite deliberately does not repeat those words, so it stays under the guard's own
threshold. Read the file itself to judge it: the inventory near the top, and the line about
what the LOGOI identity prompt carries.)*

**RULED, same day. King's words: "keep it on drive".**

Recording that needed care about which list, and the answer was not the one the guard's own error
message suggests. `GIT_AUTHORIZED` silences only the git route, and its own test insists every entry
there **still fails Drive**, because his git being private is not a reason to open the road toward
the Amazon work laptop. **Drive has no authorized list at all, by design.** So `ALLOWLIST` was the
only honest route, and `ALLOWLIST` is for files with no method in them.

That means the entry rests on the **audit**, not on the ruling. Each marker was read in place: two
are guarded filenames inside an inventory of what was rescued during the Stage M move, one is a
sentence about who controls the back end, and one sat in a line saying a prompt carries none of the
method. Nothing is reproduced. **The one weak spot was fixed rather than allowlisted around:** that
line listed the method's components in order to say a prompt lacks them, which is a smaller
disclosure than describing it but is still one, and the sentence works without it.

**Verified after:** the whole guard class green, 53 of 53, and the sync's own rules confirm Drive
really does reach the file, so the ruling is in effect rather than the test merely quietened.
Commit `9c592f98`.

**One thing his ruling did not cover, noted not acted on:** that path is not in
`logoi_gate.NEVER_LEAVES_PATHS`, so a model can still be fed the file. Drive and model retrieval are
two different roads. He ruled on the first.

---

## Still owed on this thread

- `ai-gateway.ts` does not call `routeChain` yet. The walk is built and proven but nothing uses it;
  wiring it changes how every real mission routes and what it costs, so that is King's word.
- The two unpriced tiers get real prices whenever their vendors' pages are read. Until then they
  are named every time the meter runs.
