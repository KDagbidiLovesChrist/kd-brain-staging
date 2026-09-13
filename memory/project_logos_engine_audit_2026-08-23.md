---
name: project-logos-engine-audit-2026-08-23
description: "The night the Logos engine was audited and finished: 17 confirmed findings all closed, plus the 7 Aug build hang, which was never what the comment said it was."
metadata: 
  node_type: memory
  type: project
  originSessionId: 516f60b2-b796-4a03-83ee-de543aaa4775
  modified: 2026-08-23T00:39:57.948Z
---

# The engine audit, 22 to 23 August 2026

King asked "is the engine done?" four times in one night. Each time the honest answer was
no, and each time the reason was different. This file is the record of what was actually
wrong, because the pattern in it is worth more than the fixes.

## The pattern, and it is the point

**Every single blocker was a claim that outran the code.** Not one was a crash. The engine
worked; what failed was the relationship between what it did and what it said.

- The page promised it "refuses to build on a brief it cannot ground in fact". It never
  grounded a brief. It grades the finished campaign, and a failed check STAGES the work
  anyway with a red label. **That sentence was edited during the honesty pass whose whole
  purpose was removing sentences like it, and the false clause was carried through
  verbatim.** Careful reading failed twice on the same line. That is why it now has a test.
- `prove-sovereign.ts` printed confidence numbers, asserted nothing, swallowed every error,
  and exited 0 regardless. It reported PASS under `npm test` no matter what the engine did.
  GREEN was built on top of that measurement.
- `prove-isolation.ts` asserted that a bare GET leaks no tenant name, and passed 17/17 for
  months **against a configuration the partner instance never runs**: it never set
  `LOGOS_INSTANCE_LABEL`, which `.env.klarnow` sets to "Klarnow World instance". The guard
  was right. It was simply never given the hostile input.
- The build hang's own comment named the wrong cause for sixteen days.

**The lesson: a guard is only worth what its last hostile run was worth.** Three separate
guards existed, were correct, and were passing because nobody had pointed them at the
real world.

## What was found and fixed

Audit: 4 read-only lenses, 24 findings raised, each attacked by a separate refuter,
**17 survived**. All 17 fixed across six commits (`dc9a996`, `c2deaf8`, `c924631`,
`87171c0`, `4f592e8`, plus `0ace055` and `ccc4a6d` earlier the same night).

**The dangerous one:** `/approve` and `/reject` read no status, so **a rejected mission
could be republished from its URL**, and a published one pulled back out. Fixed in the SQL
statement (`AND status = 'pending'` plus a changes check), not in the two routes, because a
check in a route is one the next route forgets to copy and a read-then-write still races.

**Also:** a Builder refusal left the previous run's approval live and approvable, so the
operator could publish a campaign the engine had just refused to stage. GREEN was
unreachable through the UI for any mission built before it was scored. Unknown ids returned
a raw 500 echoing the internal error. The login page named the client. A CSS comment in
`PAGE_STYLE` also named the client, and `PAGE_STYLE` is served to the unauthenticated login
page.

## The build hang: three causes, none of them the one in the comment

Open since 7 Aug, worked around with `standalone-server.ts`. Every prior attempt assumed
`node:sqlite`. All three real causes were found by reproducing rather than by reasoning
from the old notes.

1. **`@types/node` pinned at `^20` while the project runs Node 24.** `node:sqlite` has only
   been typed since ~22.5, so the import had no types and `next build` failed type
   checking. **Those were the same two errors filtered out of every `tsc` run for weeks as
   "pre-existing".** They were the bug.
2. **The workaround had become the blocker.** `db.ts` loaded sqlite through `createRequire`
   with the specifier built as `["node","sqlite"].join(":")` to hide it from the bundler. A
   bundler cannot resolve a computed specifier: "Cannot find module as expression is too
   dynamic".
3. **The actual hang:** `path.resolve(process.cwd(), raw)` made Turbopack trace the whole
   project, **34,328 files and 798MB of node_modules**, into the output. It was never
   hanging. It was walking the tree. Next.js 16 says so in a build warning, which is how it
   was finally found.

`next build` now exits 0 in about 15 seconds with no warnings, `next dev` is ready in
568ms, and **tsc is clean with no exceptions for the first time.**

## The bug the real types exposed, which matters most

The hand-written type declaration in `db.ts` typed `run()` as returning plain `number`. The
real signature is `number | bigint`, and **`1n === 1` is false in JavaScript**.
`resolveApprovalRequest` compares `changes` to 1 to decide whether it won the race, so a
bigint would have made the approval gate **refuse every decision, including the first**.

The same hand-written type had declared `run()` as `void` for months, which is exactly why
a conditional UPDATE looked impossible when the replay hole needed one. **A type that lies
is worse than no type**, and this one lied in the file the whole engine depends on.

## Standing decisions

- **`standalone-server.ts` stays**, and is now stated as a choice rather than a workaround.
  Both toolchains work. Every route, refusal and guard in it is proven by `prove-*.ts`
  driving real HTTP; the Next.js app is one page rendering the same data. Migrate when
  there is a reason, not because a comment says "temporary".
- **`discardedAsMisread` was kept, not deleted**, though nothing can fill it. Rounds four
  and five deliberately made every misread a visible note instead of a silent discard, and
  two prover checks assert the bucket stays empty. That is the standing guard that nothing
  is quietly thrown away. It is no longer written to the permanent log on every run.
- **Every fix was proven red-then-green**: the bug was put back and the guard watched to
  fail, then restored. After finding a prover that could not fail, shipping another
  untested one was not an option.

Related: [[project_klarnow_world_brain_2026-08-17]] · [[feedback_verify_route_by_last_run]] ·
[[feedback_coordination_on_point]]
