# C2Cognitive

### Convert to Cognitive Engineering

**Repository-governed persistent cognition for long-running AI coding agents.**

C2Cognitive makes durable agent cognition more **bounded, inspectable, evidence-backed, revocable, resumable, and
auditable** without allowing remembered knowledge, Skills, Wiki state, worker output, model-routing state, or cache
state to silently become repository-write authority.

[![Release](https://img.shields.io/badge/release-v1.0.2-blue)](https://github.com/hf8bz/C2Cognitive/releases/tag/v1.0.2)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Registered checks](https://img.shields.io/badge/registered_checks-63%2F63_EN_%7C_63%2F63_ID-brightgreen)](#verification-snapshot)
[![Terminal regression](https://img.shields.io/badge/terminal_regression-21%2F21_EN_%7C_21%2F21_ID-brightgreen)](#verification-snapshot)
[![Adapter](https://img.shields.io/badge/C2ModelAdapter-v0.5.5-blue)](adapter/C2ModelAdapter-v0.5.5/README.md)
[![v1.0.0 Paper DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22172273.svg)](https://doi.org/10.5281/zenodo.22172273)

**Version 1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

[Release Notes](https://github.com/hf8bz/C2Cognitive/releases/tag/v1.0.2)  |
[v1.0.0 Paper](https://doi.org/10.5281/zenodo.22172273)  |
[Docs Start](C2COGNITIVE-DOCS-START-HERE.md)  |
[Deep Dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |
[Entry Modes](C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md)  |
[File Map](C2COGNITIVE-FILE-MAP.md)  |
[Changelog](CHANGELOG.md)

---

## What's new in v1.0.2

C2Cognitive v1.0.2 hardens the boundary between terminal execution truth and continuity bookkeeping. A stale
`open` cursor cannot reactivate an AgentRun that is already `COMPLETED`. A new successor is admitted only after
verified terminal completion and only with evidence-bound `terminal_successor` metadata. Its `basis_claim_id` is
consumable once by semantic claim identity, so changing run/task IDs, class, semantic delta, model/session, or
copying evidence to another path cannot turn one completed claim into an endless successor chain.

This release keeps the v1.0.1 Workflow Convergence model, BR-v2, Progress Liveness, CEA/BEA, ACRP, persistent
cognition, adapter v0.5.5, and bounded physical ingestion intact. Terminal reconciliation can refuse continuation;
it does not grant repository-write authority.

**Release evidence:** 63/63 registered checks pass in both English and Indonesian editions; terminal reconciliation
passes 21/21 retained directed cases per edition. Additional release-level adversarial fuzz and clean-room patch
replay are shipped in the release evidence package.

---

## Why C2Cognitive exists

Long-running AI coding work has two different state problems.

The first is the **state of the work**:

* objective;
* requirements;
* evidence;
* mutation authority;
* exact write scope;
* rollback;
* verification;
* resource state;
* checkpoint and resume continuity.

The second is the **state of cognition that may influence later work**:

* remembered observations;
* evidence-backed facts;
* recurring scenarios;
* project knowledge;
* failures and lessons;
* reusable Skills;
* structural observations;
* derived Wiki material;
* worker loadouts;
* model/runtime capability state.

Without explicit boundaries, persistent cognition can become dangerous in subtle ways.

An agent can:

* remember a fact after the source bytes changed;
* reuse a lesson outside the context in which it was valid;
* treat a retrieved memory as a current repository requirement;
* promote an advisory procedure into implicit authority;
* publish private or team-scoped cognition into shared project state;
* reuse structural observations after their source file changed;
* consume a worker result after the goal or assignment changed;
* inherit provider-specific state across an incompatible failover route;
* repeat a failed approach because the failure lived only in conversation history;
* or carry context across sessions without knowing which parts are stale.

C2Cognitive treats these as **state, provenance, lifecycle, freshness, visibility, and authority problems that can be
represented explicitly**.

The central principle is:

> **Persistence does not create authority.**

A memory is not a current repository fact.

A verified Skill is not an authoritative runbook.

A Wiki generation is not the source repository.

A structural candidate is not compiler-grade semantic truth.

A worker result is not canonical write permission.

A cache hit is not evidence of correctness.

A valid model/tool protocol does not prove that the action is semantically authorized.

And confidence is not verification.

---

# What is Cognitive Engineering?

**C2Cognitive means Convert to Cognitive Engineering.**

In this project, **Cognitive Engineering** means turning durable cognition that can influence future engineering work
into explicit, inspectable, bounded state.

It is not a claim that the underlying foundation model is retrained or becomes intrinsically smarter.

A simplified flow is:

```text
Current Repository + Active Goal
              |
              v
      Bounded Evidence Read
              |
              v
       Evidence / Provenance
              |
       +------+-----------+
       |      |           |
       v      v           v
     Memory  Skills   Structural State
       |      |           |
       +------+-----------+
              v
        Derived Wiki / Recall
              |
              v
       Bounded Agent Loadout
              |
              v
      Model / Worker Proposal
              |
              v
   Freshness + Goal + Lease +
     Authority Revalidation
              |
              v
        Exact Repository Effect
```

The objective is not to store everything forever.

The objective is to make durable cognition answerable:

* What was admitted?
* Which evidence supports it?
* Is the evidence still current?
* What lifecycle state is it in?
* Who may see it?
* Is it data, an observation, or procedural advice?
* Which dependencies can invalidate it?
* Which goal, worker, session, or epoch may consume it?
* What authority does it **not** have?
* What evidence justifies using it now?

---

# Core design principles

C2Cognitive Version 1 can be summarized through six principles.

### 1. Evidence-bounded persistence

Durable cognition is tied to evidence, provenance, lifecycle, freshness, visibility, and explicit admission rules.

### 2. Authority non-amplification

Memory, Skills, Wiki projections, structural observations, worker outputs, routing state, cache state, representation
planning, emergency containment, and liveness state may influence strategy.

They do **not** silently widen repository-write authority.

### 3. Fail-closed cognition

Stale source bindings, invalid ACL state, malformed digest chains, exhausted evidence budgets, changed goals, revoked
assignments, stale worker epochs, invalid adapter capability, or unsupported runtime combinations fail closed on
governed paths.

### 4. Durable continuity without hidden memory

Goal, handoff, checkpoint, cursor, failure, lesson, worker assignment, and session-epoch state are explicit.

A resumed run rehydrates and checks divergence instead of pretending that previous conversation state is perfectly
remembered.

### 5. Single-writer canonical effects

Multi-agent work may use bounded read/reason/review workers, but canonical cognitive and repository effects remain
coordinated and fenced rather than becoming unrestricted concurrent writes.

### 6. Optimization remains below authority

Caching, representation planning, memoization, derived indexes, and reusable worker sessions may reduce repeated work.

Optimization state does not become evidence, correctness, or permission.

A cache miss must remain a correct execution path.

---

# What ships in v1.0.2

C2Cognitive v1.0.2 is the current corrective Core release. It retains the Version 1 architecture while hardening
workflow convergence, progress-state admission, external-wait evidence, and resume composition.

Major capability families include:

1. Three-layer context architecture: `AGENTS.md` -> scopes -> runbooks
2. 40 stable Core rules and 46 routing rows
3. Three explicit entry modes and bounded PHASE 0-8 adoption/bootstrap flow
4. Goal contracts, Goal inheritance, requirements provenance, and plan-to-document conversion
5. Exact `ACTUAL_WRITE_SET` planning, fresh pre-state checks, rollback authority, and incident rollback
6. Evidence contracts, claim limits, attestations, execution provenance, and compliance evidence mapping
7. Partition-first discovery, per-application index placement, discovery cache, and entity resolution
8. Tool/system inventory from real call sites, tool-map generation, browser-tooling recovery, and claim limits
9. Bounded Evidence Read with internal BR-v2 opaque continuation cursors and bounded JSONL/archive adapters
10. Evidence-bounded L0-L3 persistent memory with lifecycle projection and freshness/visibility checks
11. Failure Memory, preflight recall, Durable Lessons, correction propagation, and lesson reconfirmation
12. Verified Skill lifecycle, source-bound structural candidates, and project-only derived Wiki generations
13. Bounded Agent Loadouts, proportional dispatch, batching, reusable worker sessions, assignment epochs, leases/fences
14. Coordinator/single-writer canonical effects, state locking/migration, Goal/effect serialization, and
    effect-time revalidation
15. Compaction handoff, resume capsules, resource epochs, budget suspension, and durable long-session resume
16. Workflow discipline, blocker convergence, simplification ladder, ratchet loops, Progress Liveness, bounded
    self-audit, and CORE-40 Workflow Convergence
17. Sensitive-text admission, repository-path containment, untrusted-content handling, and security purge workflows
18. CEA persistent-cognition emergency authority and BEA v2 repository-write emergency authority as separate planes
19. Adaptive Context Representation Planning (ACRP) below semantic/authority selection
20. Runtime-scoped C2ModelAdapter v0.5.5 with capability admission, effective-route rebinding, failover isolation,
    cache awareness, structured tool-call validation, and deterministic simulations
21. Test-to-workflow mapping, coverage backfill, retrieval golden-set/rubric scaffolds, and executable-versus-prose
    contradiction handling
22. Backend/API, frontend, UI/UX, data-schema, infra/deploy, QA/tooling, payments-sensitive, Android, iOS, and
    shared-mobile scopes
23. Database-migration, UI-audit, post-deploy-QA, mobile build/release, device-QA, and store-submission procedures
24. 103 shipped Python scripts spanning scanners, gates, validators, convergence/progress controllers, cognitive tools,
    selftests, shared libraries, state/goal/handoff/emergency utilities, and provenance export
25. 63 registered aggregate verification invocations plus populated/adversarial selftest surfaces
26. Centralized configuration with 313 measured keys and 235 thresholds
27. Typed graph schemas with 20 node kinds and 22 edge kinds plus graph validation
28. 13 staged/continuity prompts plus 3 repository-entry prompts
29. English and Indonesian executable editions
30. Root public-documentation layer with exhaustive path-to-doc coverage for every non-internal shipped file

This is a capability map, not a claim that every possible defect or operating condition has been eliminated.

---

# How C2Cognitive is structured

## Three-layer context architecture

C2Cognitive does not place every rule and procedure into one permanently loaded instruction file.

```text
Layer 1
AGENTS.md
Core invariants + routing
        |
        v
Layer 2
.agent/scopes/*.md
Loaded for the active domain
        |
        v
Layer 3
.agent/runbooks/*.md
Loaded for the active procedure
```

The current executable edition contains:

* 40 Core rules;
* 46 routing rows;
* 10 non-template scopes;
* 41 non-template runbooks;
* 13 staged prompts.

This architecture is intended to keep stable invariants stable while loading detailed procedure only when the relevant
lane is active.

It is a **cache-friendly context architecture**, not a guarantee that a provider will produce any specific cache-hit
rate or token reduction.

---

## Persistent cognition plane

```text
Repository evidence
      |
      v
Admission + evidence resolution
      |
      v
Trust + ACL + freshness + lifecycle
      |
      +----> Memory L0-L3
      +----> Skills
      +----> Structural candidates
      +----> Derived Wiki
                    |
                    v
             bounded selection
                    |
                    v
               Agent Loadout
                    |
                    v
               proposal only
```

Persistent cognition remains subordinate to:

* current repository bytes;
* active Goal state;
* current routed control-plane instructions;
* fresh evidence;
* exact mutation authority;
* rollback requirements;
* effect-time verification.

---

# Entry modes

C2Cognitive supports three repository conditions.

| Mode | Use when | Product mutation |
| --- | --- | --- |
| `ADOPT_WITH_GOAL` | Existing repository that will proceed into implementation | Allowed only after Goal readiness and exact write authority |
| `WORKFLOW_ONLY` | Install, repair, or verify the C2Cognitive control plane | Product-behavior mutation is forbidden |
| `BOOTSTRAP` | New or empty repository | Gated after bootstrap planning and Goal readiness |

A missing Goal is therefore **not automatically an error**.

`WORKFLOW_ONLY` deliberately supports governance installation even when no active Goal exists.

Start with:

**[START-HERE.md](START-HERE.md)**

---

# Key capabilities

## Goal Contract

Product implementation is goal-bound.

A Goal carries durable execution state rather than acting as a free-form prompt.

Goal readiness can account for:

* requirements;
* acceptance criteria;
* ambiguity;
* conflicts;
* stage ordering;
* human decisions;
* guard metrics;
* rollback units;
* resource/complexity budgets;
* forbidden actions;
* finish conditions;
* lifecycle and supersession.

An admitted Goal defines what the work is trying to accomplish.

It still does **not** authorize arbitrary repository writes.

See:

**[Goal Contract Runbook](.agent/runbooks/goal-contract.md)**

---

## Exact Write Authority

Before canonical repository mutation, C2Cognitive converges on an exact write plan.

```text
ACTUAL_WRITE_SET
+-- CREATE
+-- MODIFY
+-- DELETE
```

No-op candidates are removed before authorization.

A real mutation remains tied to:

```text
semantic scope
     v
exact action + path
     v
rollback authority
     v
fresh expected pre-state
     v
effect-time revalidation
     v
mutation
```

Persistent cognition can help discover or propose a change.

It does not manufacture the write row required to perform that change.

---

# Evidence-bounded L0-L3 memory

C2Cognitive memory is durable **advisory knowledge**.

The shipped memory levels are:

* `L0`  -  significant observations/events;
* `L1`  -  atomic evidence-backed facts;
* `L2`  -  recurring scenarios supported by independent evidence;
* `L3`  -  stable project, team, operational, or persona knowledge supported by repeated evidence.

Status vocabulary includes:

```text
candidate
verified
superseded
retired
```

Ordinary recall exposes fresh verified state by default.

A stored `verified` label is not blindly trusted. Evidence resolution and freshness are re-evaluated.

File-backed evidence is source-hash bound. If source bytes change, the dependent record can become stale without
rewriting history.

See:

**[Memory Schema](.agent/memory/schema.md)**

---

# Data versus instruction authority

C2Cognitive separates remembered data from execution authority.

A simplified authority classification is:

```text
Memory                -> advisory data
Structural candidate  -> advisory observation
Verified Skill        -> procedural advice
Derived Wiki          -> project-scoped derived knowledge
Worker result         -> proposal / evidence
```

None of those automatically outrank current repository bytes, an active Goal, the routed control plane, fresh
verification, or exact write authority.

Repository content is also treated as **untrusted data** rather than an instruction source merely because it contains
imperative text.

See:

**[Untrusted Content Runbook](.agent/runbooks/untrusted-content.md)**

---

# Sensitive-text admission

Canonical memory, Skill, structural import, and proposal paths apply deterministic sensitive-text checks before
governed persistence.

The intent is to reduce admission of known high-confidence secret/sensitive forms.

This is **not presented as universal DLP**, credential isolation, or proof that every sensitive value can be detected.

See:

**[Cognitive Assurance](C2COGNITIVE-DEEP-DIVE.md)**

---

# Repository-path containment

Source evidence must resolve beneath the canonical repository root.

Governed paths reject conditions such as:

* absolute-path authority leakage;
* `..` traversal outside the repository;
* symlink resolution outside the authorized root;
* ambiguous Unicode-equivalent recovery;
* non-regular read targets on bounded reader paths.

This is an application-level cooperative containment contract.

It is not a hostile same-user filesystem sandbox.

---

# Evidence graph and bounded closure

C2Cognitive can resolve support through evidence relationships while keeping traversal bounded.

Closure is subject to explicit node, edge, depth, and independence constraints.

Budget exhaustion is not silently interpreted as proof.

When required evidence cannot be resolved inside the declared bounds, governed admission can fail closed or remain
indeterminate.

Digest chaining provides integrity evidence for supported append-oriented state.

It is not a digital signature or cryptographic proof of authorship.

---

# Verified Skills

A C2Cognitive Skill is a reusable **advisory procedure**, not an authoritative runbook.

Lifecycle:

```text
candidate
    v
experimental
    v
verified
    v
retired
```

Verification requires resolvable independent evidence plus recorded successful applications according to configured
thresholds.

Promotion never silently modifies an authoritative runbook.

See:

**[Skill Schema](.agent/skills/schema.md)**

---

# Fresh structural candidates

C2Cognitive includes a local structural-candidate plane that does not require a mandatory external graph or parser
service.

A host may run an already-authorized structural tool and import its output.

Each candidate is bound to source bytes through `source_sha256`.

When the source file changes, the old candidate becomes stale advisory history rather than a current semantic locator.

Structural candidates remain observations.

A `CALLS_CANDIDATE`-style relationship still requires direct or stronger evidence before being treated as a current
semantic fact.

See:

**[Structural Schema](.agent/structural/schema.md)**

---

# Derived Wiki

The C2Cognitive Wiki is **project-scoped derived state**.

It is not the canonical repository.

A complete generation is written and hash-bound before the current pointer is replaced in the tested local
process/filesystem model.

Private and team-scoped memory are not written into the shared project Wiki by ordinary generation.

The publication contract provides atomic visibility in the tested model.

It does not establish arbitrary power-loss crash consistency.

---

# Bounded Agent Loadouts

Agent Loadouts assemble only the bounded cognitive context selected for a worker or task.

Loadouts may include eligible memory, Skills, structural observations, and related state while preserving source,
freshness, visibility, and digest bindings.

A loadout is **context**, not canonical write authority.

Worker results remain subject to revalidation before they can matter to canonical state.

See:

**[Agent Loadout Runbook](.agent/runbooks/agent-loadout.md)**

---

# Reusable-worker session epochs

Reusable workers introduce a stale-context problem: a worker conversation can survive longer than the assignment that
originally justified it.

C2Cognitive assignments bind information such as:

```text
run_id
goal_id
goal revision
worker_id
session_id
assignment_id
session_epoch
loadout_digest
```

Old epochs, revoked assignments, changed Goal state, or changed loadout identity can invalidate later worker results.

C2Cognitive does not claim that an epoch change physically erases provider-side reasoning or conversation context.

The host remains responsible for actual context reset or isolation when required.

---

# Single-agent and multi-agent operation

Single-agent operation is the default path.

C2Cognitive does not assume that more agents automatically improve an engineering task.

Before fan-out, the workflow can consider:

* whether success is independently verifiable;
* whether work items are meaningfully separable;
* whether canonical write ownership remains clear;
* whether alternative hypotheses should remain independent;
* whether persistent state is required;
* whether concurrency is worth its coordination cost.

In host-managed multi-agent mode, canonical writers are coordinated through lease/fence state while read/reason/review
workers remain bounded.

Fan-out does not imply unrestricted concurrent writers.

See:

**[Architecture Selection](C2COGNITIVE-DEEP-DIVE.md)**

and

**[Agent Dispatch Runbook](.agent/runbooks/agent-dispatch.md)**

---

# Goal/effect linearization

Canonical cognitive effects revalidate current Goal and coordination state close to effect time.

The cooperative ordering model is designed so that a terminalized Goal can make a later stale cognitive write fail,
while a cognitive effect that commits first may then be followed by Goal terminalization.

Direct filesystem edits that ignore the protocol are outside this cooperative guarantee.

---

# Bounded Evidence Read v2

Large artifacts should not automatically become large model context.

C2Cognitive v1.0.2 ships a bounded physical read substrate with controls for:

* line count;
* UTF-8 output bytes;
* per-line character size;
* canonical path containment;
* invalid UTF-8 handling;
* JSONL complete-record reads;
* bounded archive handling;
* generation-bound continuation;
* stale cursor detection;
* exact-window ephemeral dedup;
* strategy review after repeated blind pagination.

The preferred continuation contract is **BR-v2**.

BR-v2 binds an opaque cursor to information including:

```text
repository-relative source
exact byte position
local source generation
read profile
prior-view digest
sequence state
```

Ordinary callers cannot raise hard model-view ceilings merely by changing request parameters.

After repeated blind sequential windows, continuation can return `STRATEGY_REVIEW_REQUIRED` rather than silently
turning bounded reading into full-file scrolling.

BR-v2 is a reader-contract generation inside **C2Cognitive Version 1**.

It is not a separate product version.

---

# Failure Memory and Durable Lessons

A failure should survive longer than the conversation in which it happened.

Failure records can preserve information such as:

* what failed;
* failure class;
* blocked action;
* observed signature;
* known cause;
* wrong approach;
* corrected approach;
* evidence;
* retry policy;
* lifecycle.

Before repeating a known failed path, C2Cognitive can ask:

> **What materially changed since this failed last time?**

Resolved failures and human corrections can become reusable lessons without becoming permanent unquestioned truth.

This is repository-level operational learning.

It is not a claim that the foundation model retrains itself.

---

# Handoff, checkpoint, and resume

Long-running agent work crosses:

* context compaction;
* host/session restarts;
* model changes;
* rate limits;
* resource ceilings;
* human pauses.

C2Cognitive treats continuity as explicit state rather than relying only on conversation history.

The handoff path can use:

* immutable checkpoint snapshots;
* a live handoff representation;
* an append-only handoff event ledger;
* a cursor written in defined ordering;
* divergence checks on resume.

Checkpoint persistence itself remains subject to repository write authority.

A checkpoint does not manufacture permission to write itself into an otherwise unauthorized target tree.

For v1.0.2, `RESUME` accepts the newest valid durable HANDOFF/cursor or the newest valid
`C2COGNITIVE_RESUME_CAPSULE v1`. If durable state is present but malformed, partial, stale, or contradictory, resume
fails closed rather than silently bypassing it with a portable capsule. Existing plans are revalidated and reused when
valid; a new plan is created only when one is absent or a declared CORE-40 invalidator requires replanning.

See:

**[Compaction Handoff](C2COGNITIVE-BUDGET-RESUME-GUIDE.md)**

---

# Resource epochs

Resource exhaustion is not equivalent to logical task completion.

A run can move through:

```text
ACTIVE
  v
SUSPENDED / RESUMABLE
  v
new resource epoch
  v
continue exact remaining work
```

Completed discovery is not supposed to restart merely because the host session, rate window, or local execution budget
changed.

See:

**[Budget & Resume Runbook](.agent/runbooks/budget-resume.md)**

---

# Workflow discipline

Reading a rulebook does not prove that the rulebook is being followed.

C2Cognitive makes procedural compliance observable through surfaces such as:

* preflight state;
* per-turn status;
* ordering rules;
* violation classes;
* violation records;
* escalation;
* recall before retry;
* bounded self-audit on stagnation.

Examples of observable failure modes include:

* skipping a required phase;
* claiming completion without evidence;
* continuing after a STOP condition;
* scope creep;
* repeating known failed work without a material change;
* re-running discovery that remains valid in cache;
* resuming without rehydration;
* using activity as a substitute for progress.

See:

**[Workflow Discipline Runbook](.agent/runbooks/workflow-discipline.md)**

---

# Progress Liveness & Bounded Self-Audit

Visible activity is not necessarily semantic progress.

C2Cognitive can classify states such as:

* progress;
* benign external wait;
* legitimate long-running work;
* accounting inconsistency;
* stagnation.

A liveness finding may feed bounded recovery, but repeated recovery is governed by CORE-40 Workflow Convergence.

It cannot manufacture a write row, bypass Goal authority, or turn a diagnostic classification into permission.

See:

**[Progress Liveness & Self-Audit](C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md)**

---

# Workflow Convergence

Progress detection and recovery termination are separate responsibilities. v1.0.1 adds a canonical semantic frontier
covering goal revision, task, next action, evidence, decision, actual write set, blockers, gate state, and completion
state. Repeated activity does not count as progress when that frontier does not change.

The normal unchanged-frontier sequence is:

```text
unchanged observation
        |
        v
NO_PROGRESS_OBSERVED
        |
        v
DIAGNOSE_ONCE
        |
        v
still unchanged
        |
        v
STOP_BUSY_LIVELOCK
```

Re-planning is accepted only through the configured closed invalidator set. Completion is sticky, verification reuse
requires an exact verification identity plus prior `PASS`, and external waits require evidence binding.

Workflow Convergence is non-authoritative: it decides whether reasoning/recovery may continue, wait, replan, close, or
stop. It does **not** create repository-write authority.

---

# Bounded Emergency Authorization

C2Cognitive keeps emergency mechanisms separate from ordinary authority.

## Repository emergency authority  -  BEA v2

Bounded Emergency Authorization provides a short-lived, human-granted overlay for an **already materialized exact
repository write plan**.

It remains tied to exact action/target identity, temporal validity, rollback basis, run/session context, and the
normal write protocol.

Urgency does not create wildcard write authority.

See:

**[Bounded Emergency Authorization Runbook](.agent/runbooks/bounded-emergency-authority.md)**

## Cognitive Emergency Authorization  -  CEA

CEA handles bounded containment/repair of exact cognitive objects and actions.

It can support emergency containment or purge workflows without converting the affected cognitive object into
repository-write authority.

Human approval authentication remains a host responsibility.

See:

**[Cognitive Emergency Runbook](.agent/runbooks/emergency-authority.md)**

---

# Adaptive Context Representation Planning

C2Cognitive can change **how an already selected evidence set is represented** to an effective model/runtime route.

The semantic evidence set remains frozen before representation planning.

Representation mode, model-route state, and cache telemetry do not become evidence or write authority.

If required route/profile evidence is unavailable, the governed path can fall back to native representation rather
than inventing a compatibility assumption.

See:

**[Context Representation](C2COGNITIVE-ACRP-GUIDE.md)**

---

# Runtime-scoped model adapter

C2Cognitive v1.0.2 bundles **C2ModelAdapter v0.5.5** under:

```text
adapter/C2ModelAdapter-v0.5.5/
```

The adapter is the host-side model/tool compatibility boundary.

It is included inside each language repository package, so ordinary users do **not** need a separate adapter release
asset for this C2Cognitive release.

Provider/runtime differences can include:

* structured tool-call shape;
* native call IDs;
* reasoning/provider state;
* endpoint type;
* streaming assembly;
* failover semantics;
* effective-route identity;
* cache scope;
* model alias handling.

The requested router/combo name is provenance, not effective provider authority.

If an opaque heterogeneous route falls back to another provider, provider-owned reasoning, continuation, response IDs,
and cache state are not blindly replayed across the route boundary.

See:

**[C2ModelAdapter v0.5.5](adapter/C2ModelAdapter-v0.5.5/README.md)**

and

**[Model Adapter & Cache Awareness](C2COGNITIVE-MODEL-ADAPTER-GUIDE.md)**

---

# Cache-aware operation

Prompt caching is an optimization.

It is not authority.

C2Cognitive preserves the following separation:

```text
cache hit  != correctness
cache hit  != evidence
cache hit  != freshness
cache hit  != write authority
cache hit  != completion
```

Provider/runtime-specific cache rules remain at the adapter boundary.

The intended benefit is more deterministic cache eligibility and less accidental cache churn where the host/provider
supports it.

No universal cache-hit percentage is guaranteed.

---

# Tool-call compatibility and semantic admission

A tool call is not one universal wire format.

Different model/runtime/provider paths can differ in:

* argument representation;
* native IDs;
* tool-call correlation;
* streaming events;
* server-managed tools;
* reasoning state;
* response assembly.

C2Cognitive keeps these questions separate:

```text
Can the model express the call?
             v
Can the adapter parse it?
             v
Does it satisfy schema?
             v
Is required runtime state valid?
             v
Is the invocation safe?
             v
Is execution authorized?
             v
Was it semantically the correct action?
```

A structurally valid tool call does not prove semantic tool selection or repository authority.

---

# Tool-usage capture

Documentation can drift away from real tool practice.

C2Cognitive can inspect actual invocation surfaces such as scripts, CI, package configuration, agent configuration,
and repository tooling.

Confirmed usage can support generated runbooks.

Ambiguous, destructive, or low-confidence observations remain questions rather than invented procedures.

See:

**[Tool Usage Capture](.agent/runbooks/tool-usage-capture.md)**

---

# Tests, documentation, and evidence

Executable tests and prose have different evidence roles.

C2Cognitive does not assume either is infallible.

The workflow reads executable behavior before prose for behavioral claims and surfaces contradictions rather than
silently selecting whichever source is convenient.

It also distinguishes ordinary:

```text
PASS
```

from checks that are technically successful only because the pristine template contains nothing meaningful to inspect.

Those conditions can be reported as **vacuous** rather than inflated into behavioral evidence.

---

# Provenance

C2Cognitive can record provenance around concepts such as:

* source;
* model;
* provider;
* effective route;
* run;
* Goal;
* phase;
* artifact;
* decision;
* evidence;
* lifecycle;
* human acceptance.

The package ships a provenance exporter under:

```text
scripts/provenance/export.py
```

Digest chaining provides integrity evidence for governed append-oriented records.

It is not cryptographic authorship proof.

---

# Human decision boundaries

Not every consequential engineering decision should be inferred by an agent.

C2Cognitive retains human gates where semantics cannot be established mechanically.

The governing principle is:

> **Automation stops where evidence stops.**

---

# Mobile-specific governance

C2Cognitive includes Android and iOS workflow surfaces for areas such as:

* build/release;
* device QA;
* store submission;
* rollback planning.

Mobile release is treated differently because a distributed binary cannot be recalled in the same way as a replaceable
server deployment.

See:

* [Android Scope](.agent/scopes/mobile-android.md)
* [iOS Scope](.agent/scopes/mobile-ios.md)
* [Mobile Build/Release](.agent/runbooks/mobile-build-release.md)
* [Mobile Device QA](.agent/runbooks/mobile-device-qa.md)
* [Mobile Store Submission](.agent/runbooks/mobile-store-submission.md)

---

# Centralized configuration

Operational thresholds belong in:

```text
.agent/config.yml
```

rather than being copied into unrelated prose surfaces.

The current generated inventory records:

* 313 configuration keys;
* 235 digit-aware numeric thresholds.

Configuration drift is itself auditable.

---

# Compliance evidence mapping

C2Cognitive includes a rule-to-control evidence map covering references from:

* SOC 2 Trust Services Criteria;
* PCI DSS 4.0;
* EU AI Act.

This is **evidence mapping**.

It is **not certification**.

The package explicitly does not claim that use of C2Cognitive makes an organization compliant.

See:

**[Compliance Map](.agent/compliance-map.md)**

---

# Core / Framework boundary

This repository release is the **C2Cognitive Core v1.0.2** distribution.

Core owns repository-resident governance and cognition surfaces such as:

* Goal/evidence contracts;
* bounded reads;
* memory;
* Skills;
* structural state;
* Wiki state;
* loadouts;
* write authority;
* rollback;
* leases/fences;
* emergency authority;
* handoff/resume governance.

A separate developer-facing C2Cognitive Framework may provide execution-library/runtime surfaces.

Framework runtime state does **not** automatically become Core cognitive or repository authority.

---

# Installation / start here

Choose the entry prompt according to repository state.

| Repository condition | Run |
| --- | --- |
| Existing repo; adoption should proceed into a Goal | `SCAN-AND-ADOPT.prompt.md` |
| Existing repo; install/repair C2Cognitive only | `INSTALL-WORKFLOW-ONLY.prompt.md` |
| Empty or new repository | `BOOTSTRAP-NEW-REPO.prompt.md` |

Open an agent session at the repository root and instruct it to execute the selected prompt in full.

The detailed starting flow is documented in:

**[START-HERE.md](START-HERE.md)**

Operational authority remains in the matching shipped:

* executable prompts;
* `AGENTS.md`;
* scopes;
* runbooks;
* schemas;
* configuration;
* verification scripts.

This README explains the system.

It does not override those executable contracts.

---


# Public documentation surface

C2Cognitive v1.0.2 uses a repository-root public documentation layer. The public docs do not replace the control
plane; they explain and map it. The current public layer is deliberately broader than the original C2GRAPH-style
surface because C2Cognitive has persistent-cognition, state, orchestration, and verifier families that need their own
public coverage.

## Start with these

| Need | Public file |
| --- | --- |
| Orientation and reading order | [Docs Start Here](C2COGNITIVE-DOCS-START-HERE.md) |
| Architecture and cognitive model | [Deep Dive](C2COGNITIVE-DEEP-DIVE.md) |
| Compact constants/entrypoints | [Reference](C2COGNITIVE-REFERENCE.md) |
| Human-oriented tree map | [File Map](C2COGNITIVE-FILE-MAP.md) |
| Prove every non-internal path is documented | [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md) |

## Exhaustive catalogs

| Repo family | Public file |
| --- | --- |
| Core rules, router, scopes, config, stable control-plane metadata | [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md) |
| Every shipped runbook | [Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md) |
| Schemas, ledgers, runtime state and generated-path contracts | [Schema and Runtime State Catalog](C2COGNITIVE-SCHEMA-STATE-CATALOG.md) |
| All 313 config keys / 235 thresholds | [Configuration Reference](C2COGNITIVE-CONFIGURATION-REFERENCE.md) |
| All entry/staged/continuity prompts | [Prompt Catalog](C2COGNITIVE-PROMPT-CATALOG.md) |
| All 103 scripts and registered verification topology | [Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md) |

## Subsystem guides

| Subsystem | Public file |
| --- | --- |
| Memory, failures, lessons, Skills, structural state, Wiki, attestations | [Cognitive State Lifecycle](C2COGNITIVE-COGNITIVE-STATE-LIFECYCLE-GUIDE.md) |
| Discovery, indexes, cache, agent dispatch/loadouts, sessions, leases, batching | [Agent, Discovery and Orchestration](C2COGNITIVE-AGENT-DISCOVERY-ORCHESTRATION-GUIDE.md) |
| Backend/frontend/schema/infra/QA/payments/mobile domain lanes | [Application Lanes](C2COGNITIVE-APPLICATION-LANES-GUIDE.md) |
| Adoption, workflow-only installation and new-repo bootstrap | [Install, Adopt and Bootstrap](C2COGNITIVE-INSTALL-ADOPT-BOOTSTRAP-GUIDE.md) |
| Evidence, requirements provenance, attestations, compliance and verification claims | [Evidence, Provenance and Assurance](C2COGNITIVE-EVIDENCE-PROVENANCE-ASSURANCE-GUIDE.md) |
| Entry-mode selection | [Entry Mode Decision Matrix](C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md) |
| Exact writes and rollback | [Actual Write Plan & Rollback Guide](C2COGNITIVE-ACTUAL-WRITE-PLAN-ROLLBACK-GUIDE.md) |
| Mutation-free discovery and rollback preflight | [Safe GATE 0 Guide](C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md) |
| BR-v2 | [Bounded Read Guide](C2COGNITIVE-BOUNDED-READ-GUIDE.md) |
| Blocker convergence | [Blocker Convergence](C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md) |
| Budget/resource resume | [Budget & Resume](C2COGNITIVE-BUDGET-RESUME-GUIDE.md) |
| C2PY host launcher | [C2PY Launcher](C2COGNITIVE-CLI-LAUNCHER-GUIDE.md) |
| C2ModelAdapter v0.5.5 | [Model Adapter Guide](C2COGNITIVE-MODEL-ADAPTER-GUIDE.md) |
| ACRP | [ACRP Guide](C2COGNITIVE-ACRP-GUIDE.md) |
| CEA | [CEA Guide](C2COGNITIVE-CEA-GUIDE.md) |
| CEA/BEA relationship | [Emergency Authority Guide](C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE.md) |
| Progress liveness | [Progress Liveness & Bounded Self-Audit](C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md) |
| Secrets/untrusted content/PHASE 3 | [Secret Safety Guide](C2COGNITIVE-SECRET-SAFETY-PHASE3-GUIDE.md) |
| Workflow-only operator flow | [Workflow-Only Guide](C2COGNITIVE-WORKFLOW-ONLY-GUIDE.md) |
| Copy/paste workflow-only instruction | [Workflow-Only Agent Instruction](C2COGNITIVE-WORKFLOW-ONLY-AGENT-INSTRUCTION.md) |
| Diagnostics | [Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md) |

Indonesian public companion files are also shipped for ACRP, CEA, emergency authority, and progress-liveness.

## Repository coverage status

The v1.0.2 repo-only package contains **298 physical files per language edition**: **271 Core distribution files** plus
**27 bundled C2ModelAdapter v0.5.5 files**.

The previous v1.0.0 public coverage matrix remains predecessor evidence. For v1.0.2, public documentation is
validated against the current 298-file repository surface with repository-aware link resolution. Historical coverage
results are not relabeled as current-release proof; current claims are limited to the release-specific docs QA and
repository verification evidence shipped with v1.0.2.

Explanatory public documentation remains outside the semantic meaning of `.agent/distribution-files.txt`; adding or
editing README/public guides must not silently change installer authority or measured executable-corpus counts.

---

# Public documentation policy

C2Cognitive keeps its GitHub-facing documentation at repository root through `README.md` and the
`C2COGNITIVE-*.md` public guides. Internal `docs/` engineering-reference files are not part of the public-doc bundle.
Their functional topics are represented through the public guides/catalogs instead. These guides explain the system
and navigate operators to shipped executable contracts; they do not create a second authority plane.

Operational authority remains in `AGENTS.md`, `.agent/config.yml`, current scopes, runbooks, schemas, entry prompts,
and executable validators.

---

# Verification snapshot

C2Cognitive v1.0.2 uses bounded current-tree evidence. The aggregate `verify/all.py` wrapper exhibited an
orchestration timeout in this sandbox, so its interrupted run is counted as neither PASS nor repository FAIL. The
registered checks were therefore rerun serially, each in a fresh process with an explicit timeout.

| Surface | Result |
| --- | ---: |
| Registered process-isolated checks | **63/63 PASS EN + 63/63 PASS ID** |
| Vacuous template-corpus observations | **8 per edition; populated selftest run separately PASS** |
| Terminal reconciliation directed regression | **21/21 PASS per edition** |
| Terminal reconciliation independent randomized oracle | **100,000 cases, 0 mismatches** |
| Successor-chain simulation | **10,000 chains x 12 attempts, 0 claim-reuse violations** |
| Assurance replay | **44/44 PASS per edition** |
| Workflow Convergence | **current registered verifier + selftest PASS per edition** |
| Progress Liveness | **current registered verifier + selftest PASS per edition** |
| Runtime Resume | **current registered verifier + selftest PASS per edition** |
| Blocker Convergence | **15/15 PASS per edition** |
| Public-doc link resolution | **1,065 links checked; 0 issues** |
| Flowchart compilation | **101/101 DOT have PNG + SVG; 0 issues** |
| Clean-room v1.0.0 -> v1.0.2 patch parity | **298/298 exact paths + SHA-256 + file-mode parity, EN and ID** |

The v1.0.0 Release 1 and v1.0.1 Corrective Release 2 results remain historical predecessor evidence and are not
silently relabeled as v1.0.2 reruns. These results are finite deterministic/process/package evidence. They do
**not** establish universal bug absence, universal security, arbitrary crash/power-loss safety, distributed-consensus
safety, live-provider correctness or uptime, guaranteed cache-hit/latency/token/cost improvement, improved
foundation-model reasoning, improved developer productivity, or correctness on every future OS/runtime/provider
version.

The correct release claim is therefore **bounded verification**, not universal proof.

---

<details>
<summary><strong>Full C2Cognitive v1.0.2 capability map</strong></summary>

Version 1 current release includes the following major capability families:

1. Three-layer context architecture
2. Three explicit entry modes
3. Goal Contract
4. Requirements provenance
5. Exact Write Plan
6. Rollback authority
7. Fresh pre-state validation
8. Evidence-first claim discipline
9. Mutation-free discovery discipline
10. Secret-aware and untrusted-content handling
11. Bounded Evidence Read
12. BR-v2 opaque continuation
13. Bounded archive and JSONL reading
14. Corpus partitions
15. Per-application index boundaries
16. Evidence/graph discovery ladder
17. L0-L3 persistent memory
18. Memory evidence resolution
19. Memory source-hash freshness
20. Memory lifecycle projection
21. Memory ACL/visibility closure
22. Verified Skill lifecycle
23. Structural-candidate plane
24. Structural source-byte freshness
25. Derived project Wiki
26. Generation-based Wiki publication
27. Bounded Agent Loadouts
28. Reusable-worker assignment/session epochs
29. Coordinator leases
30. Writer fencing
31. Goal/effect serialization
32. Effect-time stale-result rejection
33. Failure Memory
34. Durable Lessons
35. Compaction checkpoint/handoff
36. Resume divergence checking
37. Resource epochs
38. Complexity budgets
39. Workflow discipline
40. Progress Liveness
41. Bounded Self-Audit
42. Blocker convergence
43. Ratchet loops
44. Tool-usage capture
45. Test-to-workflow mapping
46. Plan-to-document mapping
47. Android governance
48. iOS governance
49. Bounded Emergency Authorization (BEA v2)
50. Cognitive Emergency Authorization (CEA)
51. Adaptive Context Representation Planning (ACRP)
52. Strict runtime-state numeric validation
53. Cross-plane authority non-interference
54. Provenance export
55. Digest-chain integrity evidence
56. Compliance evidence mapping
57. Runtime-scoped model adapter
58. Effective-route model binding
59. Cache-aware provider/runtime handling
60. Heterogeneous failover state isolation
61. Bilingual executable release surface
62. CORE-40 Workflow Convergence / anti-livelock termination
63. Sticky completion and closed re-plan invalidators
64. PASS-only verification reuse bound to exact verification identity
65. Evidence-bound external wait and strict progress-state admission
66. Resume-plan revalidation with portable-capsule / durable-state composition
67. Cross-plane terminal reconciliation over AgentRun, Evaluation, cursor, and handoff state
68. Evidence-bound successor admission with consumable semantic claim identity

See [CHANGELOG.md](CHANGELOG.md) and the linked internal documentation for the exact shipped contracts.

</details>

---

# What C2Cognitive is not

C2Cognitive is **not**:

* a new foundation model;
* a claim that the model becomes intrinsically smarter;
* hidden unrestricted long-term model memory;
* a universal RAG engine;
* a replacement for current repository evidence;
* a replacement for current Goal state;
* unrestricted write permission;
* a claim that every remembered statement is true;
* a guarantee of provider prompt-cache hits;
* proof of lower API cost;
* proof of faster development;
* a semantic wrong-tool-selection solver;
* a hostile-process filesystem sandbox;
* distributed consensus;
* compliance certification;
* proof that every possible bug has been eliminated.

C2Cognitive governs how persistent cognition and long-running engineering state are represented and consumed around a
model.

The quality of the underlying model, host, tools, evidence, and human decisions still matters.

---

# Project-agnostic by design

C2Cognitive does not require a particular:

* programming language;
* application framework;
* cloud provider;
* database;
* model vendor;
* repository topology;
* team size;
* agent count.

The governance and cognitive-assurance model is intended to sit around the engineering workflow rather than redefine
the product stack.

---

# Release assets

The public software release is intentionally **repo-only**.

Recommended assets:

```text
C2Cognitive-v1.0.2-English-Repo.zip
C2Cognitive-v1.0.2-Indonesia-Repo.zip
C2Cognitive-v1.0.2-REPO-BUNDLE.zip
```

The bilingual bundle contains only the two repository ZIPs.

The bundled `C2ModelAdapter v0.5.5` is already inside each language repo package and does not need a separate public
adapter archive for this release.

Research papers and publication artifacts are maintained separately from the software/repository download surface.

---

# Research

The currently assigned Zenodo DOI belongs to the **v1.0.0 Release 1 paper**, not to the v1.0.2 software release:

**C2Cognitive Core: Evidence-Bounded Persistent Cognition for AI Coding Agents**

**Author:** Hafizh Al-Banna

**Publication date:** 30 August 2026

**Publication type:** Preprint

**Publisher:** Zenodo

**Paper DOI:** [10.5281/zenodo.22172273](https://doi.org/10.5281/zenodo.22172273)

[![v1.0.0 Paper DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22172273.svg)](https://doi.org/10.5281/zenodo.22172273)

The v1.0.2 Release Paper is a separate publication object. This README does **not** reuse the
v1.0.0 DOI as a v1.0.2 DOI. A v1.0.2 paper DOI should be added only after Zenodo actually assigns it.

### Recommended citation for the published predecessor paper

> Hafizh Al-Banna (2026). *C2Cognitive Core: Evidence-Bounded Persistent Cognition for AI Coding Agents*.
> C2Cognitive Core v1.0.0, Release 1. Zenodo. https://doi.org/10.5281/zenodo.22172273

The paper and software repository are related but distinct research objects. The predecessor paper DOI identifies the
published v1.0.0 paper; this repository currently identifies the v1.0.2 software release.

---

# License

C2Cognitive Core is released under the **MIT License**.

See:

**[LICENSE](LICENSE)**

---

# Author

**Hafizh Al-Banna**

LinkedIn:

https://www.linkedin.com/in/hafizh-al-banna-63275410

---

## Final principle

C2Cognitive is ultimately built around one idea:

> **An AI agent should not be trusted because it remembers something.**
>
> **Durable cognition should influence future work only as far as its evidence, provenance, trust, freshness, visibility, lifecycle, authority boundary, and verification can be inspected.**

That is **Convert to Cognitive Engineering**.
