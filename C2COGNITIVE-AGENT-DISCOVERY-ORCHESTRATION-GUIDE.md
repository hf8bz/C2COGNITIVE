# C2Cognitive Agent, Discovery and Orchestration Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**

## Purpose

This guide covers the repo surfaces that coordinate discovery, caching, agent dispatch, reusable worker sessions,
batching, concurrency, graph/index placement, entity resolution, and bounded execution planning.

## Discovery ladder

CORE-11 defines three non-skippable stages:

```text
partitioned graph -> partitioned search -> direct read of candidate files
```

CORE-18 requires every discovery query to bind to exactly one corpus/application partition. If results mix another
product, generated code, or a legacy tree, selectivity failed; the workflow must narrow or change strategy rather
than silently merging evidence.

## Per-application index placement

CORE-34 requires an index to live beside the application it indexes in a multi-application repository. The policy is
configured under the `index` block of `.agent/config.yml` and checked by
`scripts/verify/index_scope.py`. A repository-root index is not the default for a multi-application repo.

## Discovery cache

Accepted discovery can be carried in handoff state and reused only while its invalidation/freshness conditions still
hold. CORE-36 forbids blindly rerunning an already cached query without naming why the cached result is no longer
sufficient.

## Scanners

* `scripts/scan/tooling.py` inventories environment/tooling evidence without executing candidate tools;
* `scripts/scan/census.py` inventories repository shape and coverage candidates;
* `scripts/scan/plan.py` inventories planning artifacts and extracts candidate modal/numeric/TODO evidence without
  silently promoting it into requirements.

The scanner result is evidence, not a decision.

## Agent dispatch

Single-agent operation is the default. Subagent dispatch is justified when it saves real context or permits bounded
independent investigation. Dispatch requires a defined output contract and wait bound. It does not create target
write authority.

## Loadouts

`scripts/agent/loadout.py` is a read-only context compiler. It does not itself spawn a process, allocate an LLM,
acquire a coordinator lease, or write repository bytes. Loadouts can combine bounded evidence/cognition appropriate
to a worker role while preserving trust and visibility boundaries.

## Reusable sessions and assignment epochs

`scripts/agent/session.py` and session/epoch contracts keep reusable workers from silently continuing an old
assignment after Goal or task identity changed. Reuse is therefore bound to current assignment/session identity,
not merely to the fact that a worker process is still alive.

## Coordinator lease and fencing

`scripts/agent/lease.py`, `scripts/state/lock.py`, and shared lease helpers provide cooperative local coordination.
They make split-brain/stale-writer conditions detectable within the C2Cognitive protocol. They are not an OS or
hostile-filesystem security boundary.

## Batching and budgets

The batch protocol splits large finding/file sets into bounded units with exact completed/total accounting. Resource
budgets declare caps for fan-out, concurrency, tool calls, retries, and graph writes. Exhaustion is a resumable
suspension rather than a correctness verdict.

## Entity resolution

Entity resolution distinguishes aliases/candidates from canonical identity. A low-confidence merge is a human
decision boundary rather than an invitation to collapse nodes because names look similar.

## Simplification and ratchets

Simplification is required before unnecessary abstraction, but may not remove hard gates. Autonomous ratchet loops
are valid only when output is verifiable, action reversible, horizon short, and environment bounded. Otherwise the
loop requires human/per-step review.

See [Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md), [Bounded Read Guide](C2COGNITIVE-BOUNDED-READ-GUIDE.md),
and [Progress Liveness](C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md).
