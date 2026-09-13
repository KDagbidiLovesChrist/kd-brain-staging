# Dispatch long work to a background agent by default

**King's ruling, 10 September 2026:** *"claude should dispatch to bg by default and the hmi i see
whats happening so it wont eat my bar."* And his reason, in his own words: *"this is for token
management cost efficiency for overall quality results."*

---

## The rule

**If a job is long, mechanical, or does not need judgement while it runs, hand it to a background
agent instead of doing it in the conversation.**

```
python tools/dispatch.py "the job, in plain words"
python tools/dispatch.py "the job" --wait      stay open, ring when done
python tools/dispatch.py --watch               ring for every running agent
python tools/dispatch.py --list                what has been dispatched
```

It returns immediately. **The chair is free from that moment.** Door 6 shows the agent working,
`claude logs <id>` shows what it did, and **the phone rings when it finishes** through the ntfy
channel that has existed since the Upwork alerts and had never been wired to anything that ends.

---

## Why, and his reason is the better half of it

**The obvious half is cost.** A long job done in the conversation draws every token of its own
waiting from the same weekly bar. Handed to a background agent, the chair spends nothing while it
runs.

**His half is quality, and it is the one to remember.** The bar is not just money, it is the budget
for judgement. **Every token spent watching a mechanical job is a token not available for a ruling
later in the week.** Grinding in the chair does not only cost more; it degrades the decisions that
come after, because the seat runs out sooner.

**So dispatching is not a cheaper way to do the same work. It is what protects the expensive work.**

---

## When NOT to dispatch

**Anything needing his judgement mid-run.** A background agent cannot ask him a question; it will
either guess or stop. If a job has a fork in it that only he can settle, keep it in the chair.

**Anything in the legal lane.** Ruling 10.3: contracts, IP, compliance and terms are Claude only and
do not walk down. They also do not get handed to an unattended session.

**Anything short.** The dispatch costs a couple of seconds and a register line. A one minute job is
not worth the ceremony.

---

## What the bell never carries

**The job's name and its verdict. Never its output.** ntfy's free server is public infrastructure
and a private topic is not encryption. The result stays on the machine; the phone is only told
there is something to look at.

---

## The honest limit

**A session leaving the agent list IS the completion signal.** There is no "finished" flag to read,
and inventing one would be worse than using the real thing. It means a crashed agent and a finished
agent both ring the same bell, so the message says to go and read the log rather than claiming
success.

---

**Related:** [the lanes](feedback_agent_lanes_one_working_tree.md) ·
`tools/dispatch.py` · `tools/push_kd.py` (the bell) · `tools/agents_at_work.py` (door 6) ·
`tools/plan_cost.py` (the spend decided at plan time) · `_ops/OPERATING_KD_INFRA.md`
