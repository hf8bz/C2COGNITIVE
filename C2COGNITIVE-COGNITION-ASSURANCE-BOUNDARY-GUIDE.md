# C2Cognitive | Cognitive Evidence, Recall and Assurance Non-Amplification

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** C2Cognitive-specific authority boundary.

**Existing path:** L0–L3 memory, Skills, structural candidates, Wiki and loadouts already provide bounded context. They are advisory, not fresh source verification.

**New trigger:** A long-running agent recalls a prior fact, lesson, Skill or Wiki result while planning a new assurance or implementation task.

## End-to-end process

1. Resolve current Goal and source, then request bounded recall under the existing ACL and freshness filters.
2. Treat a hit as a locator; resolve supporting evidence and source hash, lifecycle, visibility and confidence requirements again.
3. Exclude stale, retired, superseded, unsupported and inaccessible objects from ordinary actionable context.
4. Use surviving records to propose capability profiles, risks and independent test scenarios, not to assert project conformance.
5. Execute application assurance against actual current repository and environment; the real Goal and exact write set still gate mutations.
6. If a learned claim conflicts with new evidence, record a correction or retire the dependent memory through the proper lifecycle; never use recalled confidence to bypass a blocker.

### Decision / stop / recovery

Memory cannot satisfy an assurance obligation merely by existing. The source-bound evidence and execution needed for that obligation must still be independently present.

## Process diagram

```text
Current Goal/source + bounded memory recall
        |
  ACL / freshness / lifecycle / support filter
        |
  stale or inaccessible? -- yes --> EXCLUDE / retire through lifecycle
        | no
  proposal / candidate test only
        |
  fresh application-specific evidence
        |
  actual assurance gate + canonical write authority
```

## Does it change the previous process structure?

Composes the new capability/assurance lane with the existing cognition plane; does not turn memory, Wiki, Skill or provider cache into canonical authority.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a remembered payment integration test was green before a webhook handler changed. The old lesson may locate tests, but fresh execution and source-bound results are mandatory.

## Implementation references in the distribution

- `.agent/runbooks/memory-lifecycle.md`
- `scripts/memory/core.py`
- `scripts/wiki/build.py`
- `scripts/assurance/application.py`
- `AGENTS.md`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
