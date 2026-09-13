---
name: project-diagnose-method-scope-2026-09-12
description: "The speed fix, 12 Sep 2026: Diagnose is sent only the method sections a verdict uses (INPUT, THE REFUSAL, THE GATE). Measured on qwen3:8b, a first brief with a cold cache went 323.2s to 169.3s of reading, saving 153.9s. A REPEAT brief saved 0.1s, so this does not fix the slow second reply King reported."
metadata:
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-12T10:34:40.763Z
---

# The speed fix: Diagnose reads only what governs a verdict (12 Sep 2026)

**King's word:** "Let's do speed fix", approving the option as put to him: send Diagnose only the
sections it uses, leave his method untouched on disk.

**Why.** Every worker call passes through `callAI()`, which puts his whole method in front of the
worker's job description. The method is 7,766 characters. Diagnose does one job: read the founder's
sentence and either return angle, audience and offer or refuse. INPUT says what to extract, THE
REFUSAL says when to say no, THE GATE says what must pass. THE KNEEL, THE LOOP, THE STOP, OUTPUT,
REPENTANCE, THE DESCENT and THE CASCADE govern building, which Diagnose never does.

**Built (engine `b082a63`, `c08606d`).** `method.ts` gained `MethodScope` ("full" the default,
"verdict") and `trimToSections`, which SELECTS his own lines and never rewrites one. `CallAIParams`
gained optional `methodScope`, so every existing caller keeps the whole law. `diagnose.ts` asks for
"verdict". Off switch `LOGOS_METHOD_FULL_DIAGNOSE=1`, named in `.env.example`.

**Nothing was cut from his file.** `_private/logos_method_core.txt` is untouched, and the prover
checks its bytes and its modification time on every run.

**Proof.** `scripts/prove-method-scope.ts` red 12 failed, green 26 passed. It pins the three kept
sections, all seven dropped ones, that every line sent is a line of his file character for
character, that the cloud still gets nothing without `LOGOS_MATHS_TO_CLOUD`, and that builder,
critic and writer ask for no scope. `PROVERS=method-scope,diagnose,builder-gate` 3 of 3, `tsc` 0.

**Measured live on qwen3:8b, engine restarted 11:05 onto the new code:**
| | system prompt | tokens | read time |
|---|---|---|---|
| whole law, cold cache | 11,501 chars | 2,716 | 323.2 s |
| verdict scope, cold cache | 6,263 chars | 1,468 | 169.3 s |
| whole law, repeat brief | 11,501 chars | 2,716 | 0.6 s |
| verdict scope, repeat brief | 6,263 chars | 1,468 | 0.5 s |

**THE HONEST LIMIT, and it matters.** A first brief on a cold cache saves 153.9 s (2 min 34). A
REPEAT brief saves 0.1 s, which is nothing. Ollama caches the system prompt by prefix, so on brief
two the method was already costing near zero. **King's actual complaint on 12 Sep was "to slow 2nd
reply". This fix does not address that.** What makes the second reply slow is still unfound; the
candidates not yet tested are generation speed (about 2.7 tok/s), `runLocalExclusive()` serialising
behind the first call, and cache eviction when the grounding model (llama3.2) loads beside qwen3:8b
with only 3.4 GB free.

**Two measuring lessons, both mine.** The first timing run reported the whole law reading in 0.6 s
and the trim in 162.6 s, which is backwards: an aborted earlier attempt had already warmed that
exact prefix. Any A/B against a cached model must clear the cache between sides, and the two
variants share a prefix (the preamble and INPUT), so reversing the order is not enough either. And
the first attempt used `fetch` and died at exactly 300 s on `UND_ERR_HEADERS_TIMEOUT`, the same
undici cliff the engine already fixed with `node:http` (engine `d65685f`,
[first byte fix](project_engine_first_byte_fix_2026-09-11.md)). A measuring tool died of the very
problem it was measuring.

**Left open:** the slow second reply (see above), and King's own mic test, which closes 6.5.
