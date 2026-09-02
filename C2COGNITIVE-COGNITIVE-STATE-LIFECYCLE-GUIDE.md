# C2Cognitive Cognitive State Lifecycle Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

This guide consolidates the durable-cognition surfaces that are distributed across memory, failure/lesson, Skill,
structural, Wiki, attestation, session, and emergency files. Its goal is to make the whole cognitive state machine
visible from the public repository surface without treating persistence as authority.

## Durable state families

| Family | Shipped state | Executable surface | Core rule |
| --- | --- | --- | --- |
| Memory | `.agent/memory/l0.jsonl` through `l3.jsonl`, `lifecycle.jsonl` | `scripts/memory/core.py`, `panel.py` | evidence/freshness/ACL/lifecycle before reuse |
| Failures | `.agent/failures.jsonl` | recall verifier + preflight-recall runbook | CORE-35 memory-before-action |
| Lessons | `.agent/lessons.jsonl` | `scripts/lessons/decay.py` | durable correction with reconfirmation/lifecycle |
| Skills | `.agent/skills/skills.jsonl` | `scripts/skill/core.py` | verified reusable procedure remains below authority |
| Structural | `.agent/structural/matches.jsonl` | `scripts/structural/core.py` | source-bound candidate, not compiler truth |
| Wiki | `.agent/wiki/graph.jsonl`, runtime generation/current state | `scripts/wiki/build.py` | derived project-only projection |
| Attestations | `.agent/attestations.jsonl` | `scripts/verify/attestation.py` | evidence-to-claim integrity/traceability, not signature identity |
| Sessions/loadouts | lease/session/assignment state | `scripts/agent/loadout.py`, `lease.py`, `session.py` | worker output remains proposal until canonical revalidation |

## L0-L3 is a lifecycle, not a confidence ladder

The four memory levels are explicit durable stores with a shared schema and lifecycle ledger. A higher level does not
mean "more authoritative." Admission and later reuse remain bounded by source/evidence identity, trust,
visibility/ACL, freshness, lifecycle state, goal/session context, and any dependency invalidation.

## Failure memory and lessons

A costly failure is recorded so a later action can ask what materially changed before repeating it. A resolved
failure or human correction may become a reusable lesson, but lessons can age and require reconfirmation. Durable
learning is repository-level operational learning; it is not model retraining.

## Skills

A Skill is a reusable cognitive artifact with explicit validation/lifecycle state. A Skill may help select or explain
a procedure. It does not outrank `AGENTS.md`, an active routed runbook, exact write authority, or current evidence.

## Structural candidates

Structural observations are source-bound candidates. They are useful for navigation and impact reasoning only while
their source binding remains fresh. They are not presented as compiler-grade semantic truth.

## Derived Wiki

The Wiki is a derived project-facing projection. Its graph/current-generation state can be rebuilt or invalidated.
A Wiki row does not become the source repository and cannot grant mutation authority.

## Agent loadout and consumption

A loadout compiles bounded context for a worker. Worker results are tied to assignment/session epochs and remain
proposal evidence until the coordinator revalidates Goal, lease/fence, freshness, exact write plan, and current
repository state before any canonical effect.

## Emergency cognition

CEA can authorize exact containment/purge operations over governed cognitive objects under its own typed, bounded,
human-granted contract. CEA does not become repository-write authority. BEA is separately scoped to exact repository
mutations. The two planes do not inherit authority from one another.

## Security purge

`scripts/memory/security_purge.py` exists for governed sensitive-cognition purge workflows. Its presence does not
create permission to delete state; ordinary/emergency authority and exact target/effect binding still apply.

## What remains explicit

C2Cognitive does not claim that persisted cognition is automatically true, fresh, private, complete, or safe to act
on. Those properties are checked by the surrounding contracts.

See [Schema and Runtime State Catalog](C2COGNITIVE-SCHEMA-STATE-CATALOG.md),
[CEA Guide](C2COGNITIVE-CEA-GUIDE.md), and [Deep Dive](C2COGNITIVE-DEEP-DIVE.md).
