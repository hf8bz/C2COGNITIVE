# C2Cognitive v1.0.0 Deep Dive

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Provide a public technical explanation of C2Cognitive as a repository cognitive-engineering control plane:
persistent evidence-bounded cognition, explicit authority, bounded context, resumable execution, and verified
host/runtime boundaries.

### Canonical implementation sources

- [AGENTS.md](AGENTS.md)
- [C2COGNITIVE-SECRET-SAFETY-PHASE3-GUIDE.md](C2COGNITIVE-SECRET-SAFETY-PHASE3-GUIDE.md)
- [memory-lifecycle.md](.agent/runbooks/memory-lifecycle.md)
- [agent-loadout.md](.agent/runbooks/agent-loadout.md)
- [context-compaction.md](.agent/runbooks/context-compaction.md)

---

## 1. What "Convert to Cognitive Engineering" means

C2Cognitive does not claim to turn a foundation model into a new model. It moves selected cognition-related state out
of transient conversation history into explicit repository objects that can be inspected, validated, aged, superseded,
retired, recalled, and bounded by authority.

The central separation is:

```text
knowledge / memory / skill / structural observation
                     !=
authority to change repository state
```

## 2. The cognitive planes

### Evidence plane
Source paths, spans/digests, provenance, tests, observed call sites, and other artifacts that support claims.

### Memory plane
Evidence-bounded L0-L3 records with lifecycle state.

- **L0**  -  significant observation/event.
- **L1**  -  atomic evidence-backed fact.
- **L2**  -  recurring scenario with multiple independent support anchors.
- **L3**  -  stable project/team/operational/persona knowledge with repeated support.

### Skill plane
Reusable procedural advice that must satisfy the Skill contract before being treated as verified. A Skill remains
advice; it does not become repository authority.

### Structural plane
Fresh source-bound structural candidates derived from authorized structural tooling. They are advisory observations,
not truth merely because a parser found them.

### Wiki plane
Derived project-only views generated from admitted knowledge. Wiki publication is a projection and uses an explicit
current-generation pointer; it is not a new canonical authority source.

### Execution/Goal plane
Active Goal, exact write authority, run state, checkpoints, rollback state, and continuation. This plane governs
mutation and completion.

## 3. L0-L3 memory lifecycle

C2Cognitive memory is not transcript dumping. Records are bounded, typed by level, evidence-linked, and
lifecycle-managed. New records can be digest chained within their governed stream. Ordinary verified reads recheck
evidence/freshness requirements rather than trusting a historical `verified` label forever.

Lifecycle operations include record, validate, supersede, retire, and bounded aggregation. Supersession/retirement
change actionability through lifecycle state rather than silently rewriting history.

## 4. Agent loadouts and multi-agent work

C2Cognitive can build bounded loadouts from current evidence/memory/Skill state. Optional multi-agent operation is
host-managed and uses explicit selection criteria, worker/session identity, lease/ownership concepts, bounded
concurrency, and reduction. More agents do not create more authority.

Reusable worker sessions are bound to session epochs so stale worker state cannot be assumed current after a
host/session transition.

## 5. Goal and write linearization

A Goal is durable execution intent with readiness and finish conditions. It still does not authorize arbitrary writes.
C2Cognitive separates Goal admission from exact write planning and freshness/rollback checks.

This is important for long-running work: a plan can stay strategically valid while a specific file pre-state has
become stale.

## 6. Handoff and context compaction

Conversation compaction is treated as a continuity event. Handoff preserves the minimum explicit state needed to
resume, and the resumed session revalidates divergence before acting. L0-L3 memory can enrich a loadout after
continuity validation, but memory is not current execution state.

## 7. Bounded physical ingestion

BR-v2 limits the model-facing physical view and binds continuation to source generation/read profile. This prevents
"bounded retrieval" from becoming unbounded file ingestion through huge records, minified content, or archives.

## 8. Evidence, trust, and untrusted text

Repository text is not automatically instruction authority. C2Cognitive distinguishes data from trusted control-plane
instructions and has explicit sensitive-text handling. Evidence provenance and a digest are integrity evidence; they
are not publisher identity signatures.

## 9. Emergency authority

C2Cognitive separates:

- **CEA**  -  persistent cognition containment/purge authority;
- **BEA**  -  bounded repository-write emergency overlay.

The planes do not inherit each other. Both remain exact, bounded, time/session/incident scoped as required by their
contracts, and host approval identity remains a host concern.

## 10. Model-adapter boundary

The release bundles **C2ModelAdapter v0.5.5** under `adapter/`. It is distributed with C2Cognitive but remains a
host-side protocol boundary. The adapter normalizes effective model/provider/tooling behavior and cache-scoped details
without promoting provider/runtime state into cognitive or repository authority.

## 11. ACRP

ACRP changes representation after semantic selection. It is a productivity mechanism, not evidence selection and not
authority.

## 12. Progress liveness

C2Cognitive distinguishes visible activity from semantic progress. A liveness diagnosis can trigger bounded
audit/recovery; it cannot manufacture a new Goal or write row.

## 13. Verification model

The project separates executable checks from prose. `scripts/verify/all.py` registers the aggregate check surface;
dedicated selftests cover deeper finite interaction scenarios. A PASS is bounded to the check that ran. A vacuous PASS
is not treated as equivalent to populated evidence.

## 14. What C2Cognitive is not

C2Cognitive is not:

- a new foundation model;
- automatic model retraining;
- permission for unrestricted autonomous writes;
- a graph-database requirement;
- proof that prompt caching will work;
- proof of lower API cost;
- a compliance certification;
- a guarantee that all possible bugs are eliminated;
- or a substitute for human decisions where semantics remain unresolved.

## 15. Operational authority

This deep dive explains the system. The actual operational authority remains in the shipped rulebook, configuration,
scopes, runbooks, schemas, prompts, and validators. Start with
[C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md).

---

## 16. Full repository surface

The architecture above explains the major cognitive mechanisms. C2Cognitive v1.0.2 also ships a wider operational
surface: 40 Core rules, 46 routes, 10 non-template scopes, 41 non-template runbooks, 13 staged prompts, 103 Python
scripts, 63 registered verification invocations, evaluation scaffolds, runtime schemas/state, and bundled
C2ModelAdapter v0.5.5.

For exhaustive rather than conceptual coverage, use the [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md)
and the linked catalogs. This prevents the Deep Dive from becoming a 1:1 duplicate of every executable file while
still making omissions auditable.
## Terminal reconciliation in v1.0.2

Terminal execution truth now outranks stale continuity state. Successor creation is separately admitted by evidence and a consumable semantic claim identity, preventing ID rotation and repeated reconciliation from masquerading as progress.
