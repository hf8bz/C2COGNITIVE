# C2Cognitive | Ledger, Reconciliation and Period-Close Assurance

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Capability-specific assurance route.

**Existing path:** Existing exact-write and verification gates apply, but general code checks are insufficient for business-effective dates and accounting lifecycle invariants.

**New trigger:** Financial posting, journal reversal, delayed events, accounting policy, reconciled balances, backdating or a locked period exist in the adopted application.

## End-to-end process

1. Identify the actual accounting entity, ledger, policy owner, posting actor, currency and period boundary from project rules.
2. Separate event/transaction time, business-effective time, recording time and posting time. Keep as-of historical queries unambiguous.
3. Model open, soft-closed, closed and reopened states only where supported; name who may approve adjustments or reopen.
4. Specify independent oracles for balancing, immutable posted entries, idempotency, reversals and period-lock behavior.
5. Exercise permitted/denied actors, duplicate/retry, out-of-order delivery, partial settlement, backdated adjustments and close/reopen transitions.
6. Map unresolved invariants and reconciliation exceptions into assurance blockers. Changes to postings still require Goal and exact-write authority.

### Decision / stop / recovery

No generic runbook invents tax rates, payroll law or period policy. For a closed period, the action (reject, adjustment, reversing entry or reopen) must come from named project policy.

## Process diagram

```text
Business event + accounting policy
        |
  classify event/effective/posting time
        |
  period OPEN? -- no --> approved adjustment / reject / reverse per policy
        | yes                       |
  idempotent posting             policy decision
        |                          |
  independent balancing and reconciliation checks
        |
  unverified? -> BLOCKED; verified -> normal Goal completion review
```

## Does it change the previous process structure?

Deepens the existing QA/Goal route for accounting-capable applications; not a new always-on ledger, scheduler or accounting engine.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a payment arrives after month close. The workflow consults project policy; it cannot silently edit the closed journal to make reconciliation pass.

## Implementation references in the distribution

- `.agent/runbooks/accounting-policy-profile.md`
- `.agent/runbooks/ledger-invariants.md`
- `.agent/runbooks/period-close.md`
- `.agent/runbooks/reconciliation-and-recovery.md`
- `.agent/runbooks/capabilities/temporal-effective-backdate.md`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
