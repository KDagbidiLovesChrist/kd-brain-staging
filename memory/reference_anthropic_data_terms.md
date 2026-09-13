---
name: reference-anthropic-data-terms
description: "What Anthropic actually does with King's data on a consumer plan, and why a Commercial account becomes a precondition the moment client data flows."
metadata: 
  node_type: memory
  type: reference
  originSessionId: c5d66f2f-ab81-4e5f-854d-e8813d381bfd
  modified: 2026-08-28T05:07:30.122Z
---

# Anthropic data terms · verified 2026-08-10 from Anthropic's own docs

King asked "is my data in the Anthropic cloud sound, I want it all encrypted". This is the answer, pulled
from Anthropic's documentation rather than from memory.

## The short version

**Encrypted, yes. Provider-blind, no, and not purchasable on his plan.** A model cannot answer a prompt
it cannot read, so somewhere in the pipe it must be plaintext. That is physics, not policy. The same
distinction King already caught in §17 of the master prompt, pointed at Anthropic instead of at Tony's
layer.

## The facts

| Item | Reality |
|---|---|
| In transit | Encrypted, TLS 1.2 or higher. Every prompt, every file read into context, every tool output. |
| At rest | AES-256 infrastructure disk encryption, **Anthropic-managed keys**. Protects against a stolen server drive, not against the company. |
| Certifications | SOC 2 Type II, ISO 27001:2022, ISO/IEC 42001:2023. |
| **King's account type** | **CONSUMER terms for Claude Code itself.** Verified on the machine: OAuth login, personal org (`Kingdavidagb@icloud.com's Organization`). **CORRECTION 2026-08-15: a Console API key (`sk-ant-api…`) DOES exist**, held in the brain's central key store in King's home folder and, until 15 Aug, in the engine's `.env` (added 08-10 13:21). Console keys are issued by a Commercial organisation, so Commercial Terms apply to traffic on that key. **Whose org issued it is not yet verified (King to check in the Console).** The engine key line was removed on 15 Aug; V0 runs `LOGOS_LOCAL=1`. |
| Retention | **30 days if the training toggle is OFF. 5 years de-identified if it is ON.** Setting lives at claude.ai/settings/data-privacy-controls. |
| Zero Data Retention | **NOT available.** Docs explicitly exclude "Claude Free, Pro, and Max plans, including when customers on those plans use Claude Code". |
| Customer-managed keys (CMEK) | **NOT available.** Claude Platform workspaces or Claude Enterprise only, enabled by an account team. US regions only. |
| If a session is safety-flagged | Inputs and outputs up to **2 years**, classifier scores up to **7 years**, regardless of any setting. |
| Local transcripts | Claude Code stores full session transcripts **in plaintext** under `~\.claude\projects\`. On 08-10 that was **34,518 files, 1,004.9 MB, oldest 2026-06-15**, which breaks the documented 30-day default. Controlled by `cleanupPeriodDays`. |

## The settings that actually carry content (applied 2026-08-10)

Added to `settings.json` as an `env` block, plus `cleanupPeriodDays: 7`:

- `DISABLE_ERROR_REPORTING` · stack traces to a third-party tracker. **Default ON for Pro and Max.**
- `DISABLE_FEEDBACK_COMMAND` · `/feedback`, `/bug` and `/share` send conversation history including code,
  retained **5 years**, and can open an issue in a **public** repo. Sharpest content-carrying default.
- `CLAUDE_CODE_DISABLE_FEEDBACK_SURVEY` · kills the transcript-share follow-up, which uploads the
  transcript, all subagent transcripts and the raw session log, kept 6 months.

**Deliberately NOT set: `DISABLE_TELEMETRY` and `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC`.** Anthropic's
docs state both also disable the feature-flag evaluation that **Remote Control depends on**, and Remote
Control is King's existing phone door. Metrics carry no code, prompts or file paths, so disabling them
costs a working feature and buys almost nothing. Env vars load at launch, so all four take effect on the
next start.

## 🔴 The finding that matters most, for Klarnow and Theosis

**The moment the engine processes a client's data, a Commercial Anthropic account stops being an
optimisation and becomes a precondition.**

- Under GDPR the **client is the controller** and King's engine is the **processor**. That needs a written
  **Data Processing Agreement** per client, **sub-processor disclosure**, and the client informing their
  own users. Contracts, not a feature toggle. King is in Ireland, so GDPR and the Data Protection Act
  2018 apply directly.
- On **consumer terms**, if the training toggle is on, data can be retained **5 years and used to train
  models**. Running a client's users' personal data through that account puts their data under those
  terms.
- **ZDR, the fix, requires a Commercial organisation.** So does the ability to honestly tell a client
  "Anthropic does not train on this."
- **Not hypothetical.** The 08-09 sandbox work fixed **cross-tenant reads**, so multi-tenancy already
  exists and cross-tenant leakage has already happened once in testing. Put that beside the two standing
  flags, "fine print crafted to avoid alarming clients" and "Klarnow's clients must consent themselves".

**Declining the commercial upgrade was CORRECT for King's own files and is WRONG the moment a client's
data flows. Two different questions.** By [[feedback_asymptote_c_and_e_moves]] this is an E move: a lawyer
and an account upgrade. No amount of building changes it.

## 🔴 THE FOURTH ROUTE NOBODY COUNTED: CLAUDE CODE ITSELF (found 2026-08-10)

The brain's lockdown guards **git**, **Drive** and (found 08-10) **OneDrive**. It does not guard the route
that is live in every single session: **every file Claude reads is sent to Anthropic.**

`_ops\AGBIDI_CORE.md` is correctly `git-IGNORED` and `drive-SKIPPED`. Those guards keep it off GitHub and off
the work-laptop path and **do nothing about Claude reading it.** Same for
`_ops\THEOSIS_BACKEND_PIPELINE.md` and the whole of `projects\klarnow-logos-sandbox\`.

**This contradicts King's own principle 7 and §0c**, both set on 08-10: the 0-to-1 band is local **by
necessity** and must never cross the wire. **So guarded bands must be read by the LOCAL model (`ccr` →
`qwen3:8b`), not by Claude.** That is what the local band is for, and it is why the Stage 5 ledger has to be
**banded from its first run**. If Claude reads the guarded band, the local band means nothing.

**It already happened, stated rather than buried:** on 08-10 Claude read
`knowledge\klarnow\ip_protection_brief_2026-08-09.md` and `deck_narrative_2026-08-09.md` in full. Both sit in
the guarded `knowledge\klarnow\` directory, so **both have gone to Anthropic.**

**Which makes the training toggle urgent, not merely worthwhile.** That session ran on King's **consumer
OAuth**, so those files are retained **30 days if the toggle is OFF, or 5 years with training if it is ON**,
and the toggle state **has still never been checked.** Guarded Logos IP has already crossed.

**Design consequence:** "which model sees this" must be a **routing decision per band, enforced in code**,
not a preference anyone remembers. See [[feedback_verify_route_by_last_run]]: a control that depends on being
remembered is not a control.

## Foundry does not bypass this · verified 2026-08-28

King asked whether routing through Microsoft Foundry could satisfy the DPA/ZDR requirement above
instead of upgrading Anthropic directly. Checked against Microsoft's own docs and Anthropic's own docs,
not assumed.

**For Claude specifically, no.** Anthropic is confirmed as an independent data processor for the
inference itself when Claude is called through Foundry, not a Microsoft sub-processor. Microsoft's own
DPA covers only the platform and billing layer. A written DPA with Anthropic is still required either
way; Foundry adds a layer on top of the Anthropic requirement, it does not replace it. No training on
prompts or completions by default holds either way. Zero Data Retention for Claude on Foundry is
undocumented, Microsoft only clearly documents ZDR for its own OpenAI models on Foundry.

**For a Microsoft-hosted model instead of Claude, yes, genuinely.** If client-facing calls use a
Microsoft model (GPT-5.6, Phi-4, etc.) rather than Claude, Microsoft is the full processor under
standard, already-standing Product Terms, no bespoke negotiation needed, and ZDR is available via a
support ticket under an Enterprise Agreement.

**King's decision, 2026-08-28: Option C.** Keep Claude for his own work (tenant zero, unaffected by any
of this). Build a Foundry branch reserved for client tenants only, so client data goes through a
Microsoft-hosted model instead of Claude, sidestepping the Anthropic DPA requirement entirely for client
traffic. Staged build plan at `plans\find-the-right-model-lazy-pillow.md` (schema change, gateway branch,
then routing, each stage tested and shown before the next). This does not resolve King's own Claude usage
question; that track (verify the Console key's issuing org, decide on a direct Anthropic Commercial DPA)
is separate and still open.

Sources: <https://learn.microsoft.com/en-us/azure/foundry/responsible-ai/claude-models/data-privacy> ·
<https://learn.microsoft.com/en-us/answers/questions/5857666/foundry-dpa> ·
<https://platform.claude.com/docs/en/build-with-claude/claude-in-microsoft-foundry>

## What genuinely can be encrypted with a key King holds

Not the Anthropic cloud, and not Google Drive (AES-256 with Google-managed keys, not zero-knowledge).
**His own storage.** BitLocker To Go on the 2TB Crucial X9 is real AES with a password and recovery key
he controls and no provider does. Caveat that matters: BitLocker protects the drive when it is **detached
or the machine is off**. With auto-unlock on a machine left on 24/7, files are plaintext to anything
running on that machine, so the disk stops the drive walking and a login plus the constitution stop the
engine being invoked. Different locks, different doors, both needed.

## Sources

- Claude Code data usage · <https://code.claude.com/docs/en/data-usage>
- API and data retention, incl. what ZDR does not cover · <https://platform.claude.com/docs/en/manage-claude/api-and-data-retention>
- Customer-managed encryption keys · <https://platform.claude.com/docs/en/manage-claude/cmek>
- Consumer data retention · <https://privacy.claude.com/en/articles/10023548-how-long-do-you-store-my-data>
- Trust Center · <https://trust.anthropic.com>

Related: [[feedback_verify_route_by_last_run]] · [[project_klarnow_os_deal]] · [[reference_api_key_setup_sop]]
