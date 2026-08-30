# C2Cognitive Progress Liveness & Bounded Self-Audit

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Document the liveness model that distinguishes tool activity from evidence-backed semantic progress and the
bounded recovery process used when progress stalls.

### Canonical implementation sources

- [85-progress-liveness-self-audit.md](.agent/runbooks/progress-liveness.md)
- [progress.schema.md](.agent/progress.schema.md)
- [progress-liveness.md](.agent/runbooks/progress-liveness.md)
- [progress](scripts/progress/)
- [progress_liveness.py](scripts/verify/progress_liveness.py)

---

## Problem

A process can be busy without getting closer to its Goal. Tool calls, messages, retries, and CPU activity are not
sufficient evidence of progress.

## Three clocks

The runbook distinguishes multiple time concepts so a long-running legitimate operation is not automatically treated
as stagnation. The current contract reasons about semantic progress, visible/host activity, and externally justified
waiting rather than using one blunt wall-clock timeout.

## Progress frontier

Progress is represented by an evidence-backed frontier/vector. A new event counts as semantic progress only when it
advances a governed component of the work state rather than merely repeating activity.

## Trigger order

When a liveness threshold is crossed:

1. classify whether the run is making semantic progress;
2. distinguish benign wait/long-running work/accounting inconsistency from stagnation;
3. fan out bounded diagnostics where justified;
4. reduce the diagnostic results;
5. select a bounded recovery action;
6. verify that the recovery changed the relevant frontier.

## Authority boundary

A liveness finding can recommend/restructure execution. It cannot create a new Goal, invent evidence, widen
`ACTUAL_WRITE_SET`, or bypass a human decision.

## Host-survival boundary

A self-audit that depends on the current process cannot claim to survive process death unless the required state is
durably represented. Resource/session resume is handled through the separate handoff/resume contract.

## Verification

Use the progress-liveness verifier and selftest surfaces. Synthetic/finite-model PASS supports the modeled state
space; it is not proof that every real external system behavior has been enumerated.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
