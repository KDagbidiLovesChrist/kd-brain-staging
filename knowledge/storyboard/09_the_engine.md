# 9 · The engine · the thing that says no

**Parts 7 and 8 were about your own work. This part is about the thing you sell. It runs on
`:3000` with its deck on `:3200`, and its own front door describes it in five words.**

```
LOGOS
The engine that says no.
```

That is not a slogan. **The refusal is the product**, and the rest of this part is why.

---

## 9.1 What it actually does

A client writes a brief in their own words. The engine does four things with it.

```
BRIEF  -->  DIAGNOSE  -->  the GROUNDING GATE  -->  BUILD  -->  a human APPROVES
            angle            checks every            the         nothing is
            audience         claim against           campaign    published,
            offer            the brief itself        assets      sent or spent
            verdict                                              by the machine
```

**Diagnose** reads the founder's own sentence and extracts the angle, the audience and the offer.
Then it returns one of two verdicts: **`build`** or **`not_ready`**.

**The grounding gate** reads what came back and checks every specific claim against what the
founder actually said. An invention is stripped or the whole verdict is refused.

**Build** produces the campaign assets.

**Approval** is a person. Nothing is published, sent, posted or spent by the machine. Amber and
above stops and waits.

---

## 9.2 Why "not_ready" is the thing being sold

Any tool can write marketing copy. **What almost none of them will do is tell a founder their
business is not ready to be marketed.**

Every other tool in this market takes the brief and produces something, because producing
something is what looks like value. That is exactly how a founder with no audience, no traffic
and no list ends up with a beautiful campaign aimed at nobody.

**Your engine refuses.** On the record, from its own database:

```
verdicts recorded    build  8      not_ready  3
```

Three founders were told no. That is the differentiator, and it is measurable.

**It has also caught real inventions**, twice:

- `grounding.failed` × 2 in the audit log;
- the Chopiva mission, where the gate caught an invented *"9 out of 10 ratings from real people"*
  before it reached the client;
- on 12 September, an answer that invented TikTok Creator Rewards and a 10k follower threshold,
  caught on live traffic and re-asked in 30.5 seconds.

**A machine that cannot say no is a machine that will confidently say anything.**

---

## 9.3 What is actually in there

| | |
|---|---|
| workers | **6**: diagnose, builder, grounding, relay, sovereign, sovereign-adaptive |
| provers | **46** |
| tenants | **2** |
| missions | **13** |
| audit events | **195** |
| approval requests | **0** |
| campaign assets | **0** |

**The two tenants are worth naming.** One is `kd-faceless`, yours, "King David Agbidi, The
Faceless Hook Engine". The other is `prove-local-concurrency`, a prover's own tenant, which
exists because as of 11 September every prover gets its own database rather than writing into
the live one.

---

## 9.4 The gap this part exists to name

**Look at the last two rows of that table again. Zero approvals. Zero campaign assets.**

Eleven missions have been diagnosed. **Not one has ever been built and put in front of a person
to approve.** The Builder worker exists, it is 300+ lines, it has its own refusal gate wired to
the grounding check, and on this database it has never produced a single asset that reached
approval.

So the engine today is **half a product**:

- the half that **judges** is real, proven by 46 provers and by three founders being told no;
- the half that **delivers** has never completed a round trip.

That is not a criticism of the code. It is the honest state, and it decides what you can sell
today. **You can sell a diagnosis. You cannot yet sell a campaign**, because no campaign has ever
come out the other end.

---

## 9.5 What a client actually buys

Not the model. They can get a model anywhere, for nothing, in a browser tab.

They buy the four things around it:

1. **A verdict they can trust**, including the one they did not want.
2. **Grounding**: every claim checked against their own words, so nothing invented reaches them.
3. **An audit trail** that proves who acted. A header can no longer sign the log as somebody else.
4. **A gate**: nothing outward without a human.

**That is governance, not generation.** It is also the only part a competitor cannot copy by
switching to a better model next month.

---

## 9.6 What the engine refuses to spend

Two `gateway.spend_refused` events are in the log. The spend gate is not decoration: a call that
would exceed the envelope does not happen, and the refusal is recorded rather than swallowed.

That matters commercially as much as technically. **A client's bill cannot run away**, because
the machine cannot choose to spend more than it was allowed.

---

## REAL TODAY

| | |
|---|---|
| **real** | diagnose, the grounding gate, the spend gate, the audit trail, tenant isolation, 46 provers, and 3 real refusals on the record |
| **half built** | the Builder. The code exists and its gate is wired; no run has ever produced an asset that reached approval. |
| **zero** | approvals (0) and campaign assets (0). No campaign has been delivered end to end. |

⚠️ **You can sell a diagnosis today. You cannot yet sell a campaign.** The product's judging half
is proven and its delivering half has never completed a round trip.

**Proof:** read read-only from the engine's own `v0.sqlite3` on 12 September: Mission 13 rows,
11 diagnosed and 2 draft; ClarityBrief verdicts `build` 8 and `not_ready` 3; AuditEvent 195 rows
with `grounding.failed` 2 and `gateway.spend_refused` 2; ApprovalRequest 0 rows; CampaignAsset
0 rows; Tenant 2 rows, `kd-faceless` and `prove-local-concurrency`. Workers counted in
`src/lib/workers/`, provers in `scripts/prove-*.ts`.

**Next:** 10 · KD Robot *(not written yet)*
