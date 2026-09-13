---
name: project-logos-ownership-and-killswitch-2026-08-23
description: "King's stated ownership and deployment model for the Logos engine (two VPS copies, he holds the master kill switch), plus the unresolved written IP conflict it collides with"
metadata: 
  node_type: memory
  type: project
  originSessionId: f941a7f6-a22b-4ace-a4f5-ea99ada02209
  modified: 2026-08-23T10:47:26.828Z
---

# The Logos engine, ownership and the kill switch (23 Aug 2026)

## King's stated position, his own words

> "I own both engines the one i will make for kalrnow i will still be working on in their vps i will be
> working on it and 10% of the engine for whatever money it prodcues is mine automatically. the vps
> klarnow engine will be carbon copy off mine but my logos engine will be my own vps"

> "I own kill switch master key"

So the model is: **two deployments, one lineage.** King's own Logos engine on his own VPS. A carbon
copy on Klarnow's VPS which King still works on. King owns both, King holds the master kill switch,
10% of engine-produced revenue is his automatically.

Earlier the same day he also framed it as: the engine lives in his Master Brain, is called **LOGOI**,
and Klarnow is a client. People can buy the engine from him directly or through Klarnow.

## The 10% is already properly drafted, do not re-litigate it

`legal/klarnow_term_sheet_2026-08-22.md` Term 3 already defines it and it matches what King said:
"Ten percent of all amounts Klarnow receives from clients for anything the engine touches", on gross,
"No deduction for compute, hosting, salaries, marketing, commission or overhead." It is a **contract
debt**, which the term sheet notes survives anything that happens to the shares. It does not depend on
where the engine runs.

## ⚠️ The unresolved conflict, NOT settled, needs a solicitor

Three documents disagree about who owns the engine, and nothing is signed:

1. **Klarnow's Engagement Pack** (`klarnow-world/knowledge/klarnow-pack/markdown-source/00-engagement.md`):
   "all product concepts, architecture, software **created specifically for Klarnow** ... belong to
   Klarnow." Carve-out: "Any **pre-existing** tools, libraries or personal frameworks you owned before
   this engagement remain yours."
2. **King's own emailed reply** (`knowledge/klarnow/technical_response_draft.md`, recorded as sent in
   `memory/project_klarnow_os_deal.md`): "All new code written for this prototype ... **belong to
   Klarnow from the first commit**." With his own carve-out for "pre-existing tools, templates or
   frameworks".
3. **King's term sheet Term 1** (22 Aug, unsigned, private): "The engine, the source code, the prompts,
   the refusal layer and the audit log **stay my property**."

Term 1 and the sent email can only both be true if the engine counts as **pre-existing**. The evidence
on disk cuts against that: the sandbox describes itself as "Created: 2026-08-07", a "72-hour sandbox
proof ... for Klarnow beta/investor demo", built from what the build spec calls "Klarnow's own spec,
non-negotiable". Engine repo first commit 16 Aug.

King's defensible argument, which he made himself on 4 Aug: **the pattern (WAT, Logos) is pre-existing
and months old; the specific sandbox code is not.** That distinction is real but it is a question of
fact and law. **Claude must never write "pre-existing" or any settled-ownership claim into a file.**
A verifier caught exactly that attempt on 23 Aug: "pre-existing" is the operative trigger of the
counterparty's carve-out, so asserting it would decide the case in the file every session reads first.

## The architectural consequence King accepted

A carbon copy on Klarnow's VPS **removes the suspend-the-endpoint remedy** that Term 1 relies on
("this is the only remedy you can use without a court, and you cannot fund a court. MUST HAVE"). King
was told this plainly and answered "I own kill switch master key", i.e. the copy must carry a licence
check he controls, so it can be switched off even on hardware he does not own.

## The live technical gap this creates

`standalone-server.ts` (verified 23 Aug): per-tenant tokens exist (`LOGOS_TENANT_TOKENS`, added 22 Aug)
but are **read-only by design**. Line 818: a tenant token "must never move a mission, spend the gateway
or append to the audit log." `authorised()` accepts **operator scope only**, so every POST needs the
master token. Because `klarnow-world` must POST (`/command`, `/diagnose`, `/build`, `/approve`,
`/reject`), it was given the operator token.

**Verified today: Klarnow's `LOGOS_TOKEN` and the engine's `SANDBOX_TOKEN` for the :3100 instance are
the same value** (proven by matching sha256, no secret printed). King's client holds King's master key.
There is no per-client revocation today: switching Klarnow off means killing the whole process.

Closing this needs a **tenant-scoped write credential**: a client key that runs only its own missions,
cannot read other tenants, cannot act as operator, and can be revoked individually. That revocation is
the kill switch King is asking for.

## ✅ CLOSED, 23 Aug. Switch 1 built, proven and live.

`LOGOS_CLIENT_KEYS` added to `standalone-server.ts`: a client key grants a SET of worlds (a reseller
runs a portfolio, not one tenancy), can write only inside them, cannot act as operator, cannot reach
`/gateway/`, and is revoked by removing one entry. New prover `scripts/prove-client-keys.ts`, **20/20**,
boots a real server on a throwaway database and actually attempts each attack. **Full suite 7/7.**

Three real holes it closed, none of which were the one being looked for:
- **The id bypass.** Both read routes accept a tenant id OR a slug, so a scope check against the
  caller's raw string is walked straight past by sending the id. The check now resolves the tenant
  first and compares the resolved slug. The prover tests this specifically.
- **`/command` fell back to the FIRST tenant** when none was named. Harmless for King on his own
  engine, a cross-tenant write for anyone else. A client key must now name its world.
- **A regression Claude introduced and a prover caught**: the ownership check called `getMission()`,
  which THROWS on an unknown id, turning `POST /sovereign/<unknown>` from a reasoned refusal into a
  mangled 404. Fixed by leaving the operator path completely untouched (no lookup, no throw) so only a
  scoped key pays for the check. `prove-sovereign` went 13/1 → **14/0**.

**The live change, 23 Aug:** the :3100 instance's `SANDBOX_TOKEN` was **rotated**, because issuing a
new client key is worthless while the partner still knows the old master key. Klarnow's
`klarnow-world/.env` now holds a scoped client key over klarnow, chopiva and clypme. Verified live:
the partner brain still reads its three worlds; the **old master key now returns 401 everywhere**; the
partner key cannot open the operator console (401) and cannot spend the gateway (403). Backups:
`engine/.env.klarnow.bak-pre-clientkey`, `klarnow-world/.env.bak-pre-clientkey`.

Also fixed in passing: the :3100 process had been serving **HTTP 500 on every request** (a stale
process, not a config fault, proven by booting the same config clean on a spare port). The restart
cleared it.

**Switch 2 (a licence check for a carbon copy on Klarnow's own VPS) is NOT built.** King was told
plainly that once a client holds the source, a licence check can be removed and rebuilt, so it is a
deterrent and a contractual hook rather than an unbreakable lock. It should be paired with the licence
wording in the term sheet, not relied on alone.

## Still open, and ageing badly

`memory/project_klarnow_os_deal.md` has carried a "⚠️ CRITICAL, NOT YET ACTIONED" flag since 4 Aug:
Klarnow's team is still expecting the GitHub push of King's OS agreed on the 3 Aug call, which King
correctly decided on 4 Aug never to send (the WAT and Logos prompts stay secret, rebuild fresh instead).
**He still needs to tell them.** 19 days open as of 23 Aug.

Related: [[project-klarnow-os-deal]] · [[project-klarnow-world-brain-2026-08-17]] · [[project-logos-engine-audit-2026-08-23]]
