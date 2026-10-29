# C2Cognitive | Application Capability Profile and Assurance Completion

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Conditional completion-gate extension.

**Existing path:** Previously described Goal acceptance, explicit write planning and test evidence remain the foundation. A successful build or unit test does not, by itself, prove all required application behavior.

**New trigger:** A real application has functional, security, integration, accounting, accessibility or operational behavior that must be accepted for release.

## End-to-end process

1. Build a source-backed capability profile with explicit `true`, `false` or `unknown` for each supported capability.
2. Validate the profile. Critical unknown capabilities, including authorization, payments and tenant isolation, cannot silently become false.
3. Generate required obligation IDs from the baseline and all capabilities actually marked true; the initial generated rows are blocked pending evidence.
4. Bind each obligation to a real requirement, build, actor, environment, independent expected result and exact evidence.
5. Classify each as verified, evidence-backed not applicable with named authority, or blocked with dependency.
6. Explicitly invoke the completion gate for this project. Missing, invalid or blocked obligations keep this assessment non-ready; normal write and approval gates still apply separately.

### Decision / stop / recovery

`scripts/assurance/application.py` implements `validate-profile`, `required`, `generate`, `validate-obligations` and `gate`. A ready assurance result is not permission to deploy.

## Process diagram

```text
Actual project profile
        |
  validate true/false/unknown
        |
  required obligation IDs
        |
  actual test + scoped evidence
        |
  invoke completion gate
        |
  valid and all mandatory resolved?
        | no -> BLOCKED / INVALID
        | yes
  readiness only (not deployment permission)
```

## Does it change the previous process structure?

Provides an explicit post-verification readiness decision when the operator or host invokes the application assurance CLI. It can block an applicable completion claim, but it does not automatically intercept every Goal or change write authority.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a marketplace declares `payments=true`, `multi_tenant=true`. A successful purchase UI test cannot close payment idempotency, webhook verification or cross-tenant denial obligations.

## Read-only / bounded entry example

```sh
python3 -B scripts/assurance/application.py required <project-profile.json>
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `scripts/assurance/application.py`
- `scripts/assurance/evidence.py`
- `.agent/runbooks/application-capability-profile.md`
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
