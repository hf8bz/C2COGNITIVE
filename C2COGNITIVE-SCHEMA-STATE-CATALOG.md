# C2Cognitive Schema and Runtime State Catalog

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

This public reference inventories the non-runbook, non-scope `.agent/` surfaces that define durable state,
validation shape, generated/runtime paths, and control-plane metadata in C2Cognitive v1.0.0.

## Complete inventory

| File | Role |
| --- | --- |
| [`.agent/attestations.jsonl`](.agent/attestations.jsonl) | Release-claim attestation ledger. |
| [`.agent/attestations.schema.md`](.agent/attestations.schema.md) | Attestation integrity/traceability schema; not a digital-signature claim. |
| [`.agent/bounded-emergency-authority.schema.md`](.agent/bounded-emergency-authority.schema.md) | Repository-write BEA proposal/grant/effect contract. |
| [`.agent/compliance-map.md`](.agent/compliance-map.md) | Evidence mapping to selected control frameworks; not certification. |
| [`.agent/config.yml`](.agent/config.yml) | Central project, tooling, index, mobile, partition, exclusion, and threshold configuration. |
| [`.agent/context-representation.schema.md`](.agent/context-representation.schema.md) | ACRP profile/plan schema for authority-neutral representation optimization. |
| [`.agent/core-baseline.md`](.agent/core-baseline.md) | Baseline reference used to preserve stable Core rules during adoption/evolution. |
| [`.agent/counts.generated.json`](.agent/counts.generated.json) | Generated measured-count snapshot checked against live measurements. |
| [`.agent/distribution-files.txt`](.agent/distribution-files.txt) | 259-file executable/control-plane distribution manifest. |
| [`.agent/draft/.gitkeep`](.agent/draft/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/emergency-authority.schema.md`](.agent/emergency-authority.schema.md) | CEA persistent-cognition emergency authorization contract. |
| [`.agent/failures.jsonl`](.agent/failures.jsonl) | Append-oriented failure-memory ledger. |
| [`.agent/failures.schema.md`](.agent/failures.schema.md) | Failure-record shape, classes, retry/change evidence, and lifecycle. |
| [`.agent/goals/.gitkeep`](.agent/goals/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/goals.schema.md`](.agent/goals.schema.md) | Goal ledger/document schema and workflow-only goal-free exception semantics. |
| [`.agent/graph/.gitkeep`](.agent/graph/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/graph/schema/edges.md`](.agent/graph/schema/edges.md) | Typed graph edge-kind schema. |
| [`.agent/graph/schema/example.jsonl`](.agent/graph/schema/example.jsonl) | Graph-schema example corpus used for validation. |
| [`.agent/graph/schema/nodes.md`](.agent/graph/schema/nodes.md) | Typed graph node-kind schema. |
| [`.agent/handoff.schema.md`](.agent/handoff.schema.md) | Durable handoff, cursor, ledger/event, and continuity contract. |
| [`.agent/lessons.jsonl`](.agent/lessons.jsonl) | Durable lesson ledger. |
| [`.agent/lessons.schema.md`](.agent/lessons.schema.md) | Lesson lifecycle, provenance, reconfirmation, and anti-pattern schema. |
| [`.agent/memory/l0.jsonl`](.agent/memory/l0.jsonl) | L0 memory ledger. |
| [`.agent/memory/l1.jsonl`](.agent/memory/l1.jsonl) | L1 memory ledger. |
| [`.agent/memory/l2.jsonl`](.agent/memory/l2.jsonl) | L2 memory ledger. |
| [`.agent/memory/l3.jsonl`](.agent/memory/l3.jsonl) | L3 memory ledger. |
| [`.agent/memory/lifecycle.jsonl`](.agent/memory/lifecycle.jsonl) | Memory lifecycle/supersession ledger. |
| [`.agent/memory/schema.md`](.agent/memory/schema.md) | L0-L3 memory and lifecycle schema. |
| [`.agent/model-adapter.schema.md`](.agent/model-adapter.schema.md) | Host adapter capability evidence schema through capability v6. |
| [`.agent/prefix.lock`](.agent/prefix.lock) | Locked router-prefix representation used to detect silent router drift. |
| [`.agent/progress.schema.md`](.agent/progress.schema.md) | Progress-liveness state, clocks, classifications, and bounded self-audit contract. |
| [`.agent/provenance.schema.md`](.agent/provenance.schema.md) | Provenance record and digest-chain schema used by export tooling. |
| [`.agent/requirements.schema.md`](.agent/requirements.schema.md) | Requirement provenance, acceptance, and guard-metric schema. |
| [`.agent/resume-capsule.schema.md`](.agent/resume-capsule.schema.md) | Portable resource/session suspension capsule contract. |
| [`.agent/routes.yaml`](.agent/routes.yaml) | Machine-checkable routing table mirror. |
| [`.agent/rule-registry.md`](.agent/rule-registry.md) | Stable rule registry and preservation metadata. |
| [`.agent/runs/.gitkeep`](.agent/runs/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/runs.schema.md`](.agent/runs.schema.md) | AgentRun execution ledger schema. |
| [`.agent/runtime-artifacts.txt`](.agent/runtime-artifacts.txt) | Declared runtime-created paths used to distinguish expected absence from broken references. |
| [`.agent/skills/schema.md`](.agent/skills/schema.md) | Verified Skill record schema. |
| [`.agent/skills/skills.jsonl`](.agent/skills/skills.jsonl) | Skill ledger. |
| [`.agent/state/.gitkeep`](.agent/state/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/structural/matches.jsonl`](.agent/structural/matches.jsonl) | Structural candidate ledger. |
| [`.agent/structural/schema.md`](.agent/structural/schema.md) | Source-bound structural-candidate schema. |
| [`.agent/toolmap.schema.md`](.agent/toolmap.schema.md) | Observed tool-call-site/tool-usage map schema. |
| [`.agent/wiki/generations/.gitkeep`](.agent/wiki/generations/.gitkeep) | Tracked empty directory placeholder; runtime content is created only by the owning workflow. |
| [`.agent/wiki/graph.jsonl`](.agent/wiki/graph.jsonl) | Derived Wiki graph surface. |

## State families

### Goal and execution state

Goal state is represented through the Goal schema plus runtime Goal artifacts. Execution state can be recorded as
AgentRun records. Neither a Goal nor a run record automatically grants write authority.

### Continuity state

Handoff and resume-capsule contracts preserve work across context compaction, host/session boundaries, rate limits,
and run-budget suspension. Runtime paths are explicitly declared so a missing not-yet-created artifact is not
confused with a broken shipped reference.

### Cognitive state

The L0-L3 ledgers, lifecycle ledger, Skills, structural candidates, Wiki graph, failures, lessons, and attestations
are durable cognition or integrity surfaces. They remain subordinate to trust, ACL/visibility, freshness, source
binding, Goal state, and ordinary write authority.

### Graph state

Node and edge schemas define the typed graph vocabulary. The example graph is validation input; it is not a claim
that every target repository already contains meaningful graph state.

### Emergency and optimization state

CEA, BEA, progress-liveness, ACRP, and host-adapter capability schemas are separate contracts. They intentionally do
not inherit authority from one another.

## Runtime-created paths

`.agent/runtime-artifacts.txt` is the canonical declaration of paths that are expected to be created later by
runtime procedures. Examples include handoff/lock state, Goal ledgers, adoption drafts, tool maps, requirements,
golden retrieval data, derived Wiki current state, provenance exports, and local lock/head files.

The path declaration does not authorize creation. The owning workflow must still satisfy its write contract.

See [Cognitive State Lifecycle Guide](C2COGNITIVE-COGNITIVE-STATE-LIFECYCLE-GUIDE.md) and
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md).
