# C2Cognitive Budget Suspension & Resume Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain how a long-running run survives resource exhaustion without pretending that exhaustion is logical
completion and without replaying already verified phases.

### Canonical implementation sources

- [budget-resume.md](.agent/runbooks/budget-resume.md)
- [context-compaction.md](.agent/runbooks/context-compaction.md)
- [resume-capsule.schema.md](.agent/resume-capsule.schema.md)
- [handoff.schema.md](.agent/handoff.schema.md)
- [98-compaction-handoff.prompt.md](prompts/98-compaction-handoff.prompt.md)
- [99-session-resume.prompt.md](prompts/99-session-resume.prompt.md)

---

## Completion and resources are independent

A task can be incomplete while the current context window, tool budget, rate limit, process lifetime, or host session
is exhausted. C2Cognitive represents that condition as resumable state rather than completion.

```text
ACTIVE
  |
  +-- logical done -------------> COMPLETE (after verification)
  |
  +-- resource boundary reached > SUSPENDED / RESUMABLE
                                      |
                                      v
                              new resource epoch
                                      |
                                      v
                              resume exact remaining work
```

## Mandatory continuity state

A bounded handoff/resume capsule can carry active objective/Goal, stage, completed work, remaining work, evidence,
decisions, blockers, changed paths, rollback state, budget state, and next action. The canonical schema - not
conversation memory - defines what the checkpoint means.

## Resource epochs

A new host/session can be a new resource epoch without being a new logical project. Completed PHASE 0-3 discovery is
not supposed to replay merely because the host process restarted, provided the required evidence and freshness checks
still support reuse.

## Resume order

1. Resolve the C2PY launcher for the new host/session.
2. Validate the resume capsule/handoff shape.
3. Re-establish Goal/run identity.
4. Check repository divergence and freshness.
5. Revalidate authority-bearing state.
6. Rehydrate only the bounded context needed for the next action.
7. Continue from the exact remaining unit.

## Emergency zero-tool fallback

The current runbook explicitly distinguishes a moment when no tool can be run. That does not authorize invented
persistence. Preserve the minimum bounded handoff in the host/session channel available, then materialize canonical
state only when authority and tooling return.

## What resume must not do

- recreate completed work because conversation memory is gone;
- assume old write authority is still fresh;
- turn a handoff into permission to mutate;
- treat L0-L3 memory as current execution state;
- or label resource exhaustion as success.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
