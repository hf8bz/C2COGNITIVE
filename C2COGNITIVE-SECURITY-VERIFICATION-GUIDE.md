# C2Cognitive | Bounded Security Testing and Failure Lineage

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Scoped QA gate extension.

**Existing path:** Security requirements and operator approval already govern sensitive tests. A single retest should not erase a prior failure without a linked result.

**New trigger:** An authorized application security lane selects SAST, DAST, fuzz, red-team or dependency checks for a named subject and environment.

## End-to-end process

1. Agree exact targets, accounts, test classes, effect scope and authorization reference; do not inherit another project’s permission.
2. Create a test plan bound to run ID, scope ID and source SHA-256.
3. Run only tools and scenarios permitted for the environment. Unavailable tool, device or credentials means NOT-RUN.
4. Record PASS, FAIL, NOT-RUN, NOT-VERIFIED or N/A per planned test with bounded, sanitized evidence references.
5. Retest through a new row with `retest_of`. Carry the same `defect_id` through unresolved descendants; N/A or NOT-RUN cannot erase an open failure.
6. Validate the ledger and attach unresolved findings to assurance obligations; only a proper matching PASS retest can close the lineage.

### Decision / stop / recovery

The validator checks structured accounting of results; it does not execute SAST/DAST/pentest by itself or prove authorization. `--require-complete` enforces full planned accounting.

## Process diagram

```text
Authorized test plan + source hash
        |
  run permitted SAST/DAST/fuzz/redteam
        |
  record PASS / FAIL / NOT-RUN / NOT-VERIFIED / N/A
        |
  previous FAIL? -- yes --> linked retest + same defect ID
        |                             |
  validate lineage and accounting <--+
        |
  unresolved defect -> BLOCKED; matching PASS -> review closure
```

## Does it change the previous process structure?

Adds a stricter result-accounting gate and failure-history continuity. Existing security scope, product-write restrictions and release approval remain intact.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: IDOR test A fails; the next test is unavailable. Recording NOT-RUN does not close A. After a fix, a linked matching PASS retest can close the defect.

## Read-only / bounded entry example

```sh
python3 -B scripts/verify/security_ledger.py --plan <plan.json> --ledger <results.jsonl> --require-complete
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `.agent/runbooks/security-testing.md`
- `.agent/runbooks/security-verification.md`
- `scripts/verify/security_ledger.py`
- `.agent/runbooks/comprehensive-qa-audit.md`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
