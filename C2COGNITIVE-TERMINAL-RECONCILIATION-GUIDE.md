# C2Cognitive Terminal Reconciliation and Successor Admission

## Why this exists

A completed run can be terminal in the execution plane while an older CURSOR/HANDOFF record still says `open`.
C2Cognitive v1.0.2 resolves that conflict in favor of execution truth and fails closed on ambiguity.

## Rules

1. Exact AgentRun `COMPLETED` forbids same-run resume.
2. Verified terminal completion is required before a successor can be admitted.
3. A new run/task ID alone is not semantic progress.
4. Successor evidence uses a closed class, semantic delta, exact file digest, and literal `basis_claim_id`.
5. `basis_claim_id` is consumable once by claim identity; proposal reshaping or evidence copying cannot reuse it.
6. Continuity/audit-only planes cannot be the sole substantive basis for a successor.
7. Free-text "check again" reasons are not completion invalidators.
8. Class-specific metadata is mutually exclusive; stray invalidator/owner fields fail closed.
9. Terminal reconciliation never creates write authority.

## Executable surfaces

- `scripts/lib/c2terminal.py` - terminal truth and successor admission.
- `scripts/handoff/validate.py --require-resumable` - strict resume validation.
- `scripts/handoff/terminal_reconcile.py` - operator-facing terminal gate.
- `scripts/selftest/terminal_reconciliation.py` - retained directed regression.
- `scripts/verify/terminal_reconciliation.py` - static integration verifier.

## Typical state flow

```text
CURSOR open -> AgentRun lookup -> IN_PROGRESS -> normal resume validation
                            \-> COMPLETED -> same-run resume rejected
                                          \-> verified terminal?
                                               no  -> successor fail-closed
                                               yes -> terminal_successor admission
                                                       \-> claim unused -> allow candidate
                                                       \-> claim consumed -> reject
```

See also `C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md`, `C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md`, and
`C2COGNITIVE-TROUBLESHOOTING.md`.
