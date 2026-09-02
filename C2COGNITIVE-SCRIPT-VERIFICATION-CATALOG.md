# C2Cognitive Script and Verification Catalog

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

C2Cognitive v1.0.2 ships 103 Python files under `scripts/`. The scripts are not one undifferentiated execution pool:
pre-authority scanners are intentionally narrow, mutating tools have their own authority contracts, validators fail
closed, and selftests exercise populated/adversarial states that a pristine template may not contain.

## Script families

| Directory | Public role |
| --- | --- |
| `scripts/agent/` | Host-neutral agent coordination, adapter capability, representation, lease, loadout, and session tools. |
| `scripts/budget/` | Resource-budget accounting and suspension checks. |
| `scripts/convergence/` | Workflow-convergence semantic-frontier watcher and classification surface. |
| `scripts/emergency/` | CEA/BEA proposal, validation, and effect tooling. |
| `scripts/goal/` | Goal gate/projected state and Goal mutation tooling. |
| `scripts/graph/` | Typed graph validation. |
| `scripts/handoff/` | Handoff validation and portable resume-capsule tooling. |
| `scripts/install/` | Target/template rollback preflight and exact plan/action verification. |
| `scripts/interview/` | Human question queue emission and authorized answer handling. |
| `scripts/jsonl/` | Generic JSONL validation. |
| `scripts/lessons/` | Lesson reconfirmation/decay checks. |
| `scripts/lib/` | Shared standard-library helper modules used by shipped scripts. |
| `scripts/memory/` | L0-L3 memory validation/operations, operator panel, and security purge support. |
| `scripts/progress/` | Runtime progress-liveness watcher. |
| `scripts/provenance/` | Provenance export and optional write/signing surface under explicit authority. |
| `scripts/read/` | Bounded text, JSONL, and archive physical-read adapters. |
| `scripts/scan/` | Target-read-only tooling, repository census, and planning-artifact scanners. |
| `scripts/selftest/` | Populated/adversarial regression harnesses for mechanisms that may be vacuous in a pristine template. |
| `scripts/skill/` | Verified Skill validation/lifecycle tool. |
| `scripts/state/` | Local state lock/fencing and schema migration tools. |
| `scripts/structural/` | Structural-candidate validation/lifecycle tool. |
| `scripts/verify/` | Fail-closed corpus, contract, identity, authority, hygiene, and integrity verifiers. |
| `scripts/wiki/` | Derived Wiki validation/build tool. |

## Complete 103-file script inventory

| Script | Family | Public role |
| --- | --- | --- |
| [`scripts/agent/adapter_capability.py`](scripts/agent/adapter_capability.py) | `agent` | Host model-adapter capability evidence admission/validation. |
| [`scripts/agent/context_representation.py`](scripts/agent/context_representation.py) | `agent` | ACRP profile/plan runtime surface. |
| [`scripts/agent/lease.py`](scripts/agent/lease.py) | `agent` | Coordinator lease/fence management surface. |
| [`scripts/agent/loadout.py`](scripts/agent/loadout.py) | `agent` | Read-only context/loadout compiler; does not itself spawn agents or grant write authority. |
| [`scripts/agent/session.py`](scripts/agent/session.py) | `agent` | Worker/session assignment epoch validation and session-state operations. |
| [`scripts/budget/check.py`](scripts/budget/check.py) | `budget` | Resource-budget accounting and suspension checks. |
| [`scripts/emergency/bounded_authority.py`](scripts/emergency/bounded_authority.py) | `emergency` | CEA/BEA proposal, validation, and effect tooling. |
| [`scripts/emergency/cognitive_authority.py`](scripts/emergency/cognitive_authority.py) | `emergency` | CEA/BEA proposal, validation, and effect tooling. |
| [`scripts/emergency/cognitive_effect.py`](scripts/emergency/cognitive_effect.py) | `emergency` | CEA/BEA proposal, validation, and effect tooling. |
| [`scripts/goal/gate.py`](scripts/goal/gate.py) | `goal` | Goal gate/projected state and Goal mutation tooling. |
| [`scripts/goal/mutate.py`](scripts/goal/mutate.py) | `goal` | Goal gate/projected state and Goal mutation tooling. |
| [`scripts/graph/validate.py`](scripts/graph/validate.py) | `graph` | Typed graph validation. |
| [`scripts/handoff/capsule.py`](scripts/handoff/capsule.py) | `handoff` | Handoff validation and portable resume-capsule tooling. |
| [`scripts/handoff/validate.py`](scripts/handoff/validate.py) | `handoff` | Handoff validation and portable resume-capsule tooling. |
| [`scripts/install/preflight.py`](scripts/install/preflight.py) | `install` | Read-only by default preflight for target/template identity, rollback basis, exact plan operations, and per-action expected state. |
| [`scripts/interview/ask.py`](scripts/interview/ask.py) | `interview` | Human question queue emission and authorized answer handling. |
| [`scripts/jsonl/validate.py`](scripts/jsonl/validate.py) | `jsonl` | Generic JSONL validation. |
| [`scripts/lessons/decay.py`](scripts/lessons/decay.py) | `lessons` | Lesson reconfirmation/decay checks. |
| [`scripts/lib/c2common.py`](scripts/lib/c2common.py) | `lib` | Shared helper module `c2common` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2emergency.py`](scripts/lib/c2emergency.py) | `lib` | Shared helper module `c2emergency` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2epoch.py`](scripts/lib/c2epoch.py) | `lib` | Shared helper module `c2epoch` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2lease.py`](scripts/lib/c2lease.py) | `lib` | Shared helper module `c2lease` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2progress.py`](scripts/lib/c2progress.py) | `lib` | Shared helper module `c2progress` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2read.py`](scripts/lib/c2read.py) | `lib` | Shared helper module `c2read` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2read_v2.py`](scripts/lib/c2read_v2.py) | `lib` | Shared helper module `c2read_v2` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2representation.py`](scripts/lib/c2representation.py) | `lib` | Shared helper module `c2representation` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/lib/c2security.py`](scripts/lib/c2security.py) | `lib` | Shared helper module `c2security` used by shipped tools; helper code does not by itself grant repository authority. |
| [`scripts/memory/core.py`](scripts/memory/core.py) | `memory` | L0-L3 memory validation and governed memory operations. |
| [`scripts/memory/panel.py`](scripts/memory/panel.py) | `memory` | Operator-facing memory inspection/control surface. |
| [`scripts/memory/security_purge.py`](scripts/memory/security_purge.py) | `memory` | Governed sensitive-cognition purge support under emergency/ordinary authority contracts. |
| [`scripts/progress/watch.py`](scripts/progress/watch.py) | `progress` | Progress-liveness classification/watch surface. |
| [`scripts/provenance/export.py`](scripts/provenance/export.py) | `provenance` | Provenance JSONL to W3C PROV-O JSON-LD export with digest-chain checks. |
| [`scripts/read/archive.py`](scripts/read/archive.py) | `read` | Bounded ZIP archive/member inspection. |
| [`scripts/read/core.py`](scripts/read/core.py) | `read` | Preferred bounded text reader using the BR-v2 contract. |
| [`scripts/read/jsonl.py`](scripts/read/jsonl.py) | `read` | Complete-record bounded JSONL reader. |
| [`scripts/scan/census.py`](scripts/scan/census.py) | `scan` | Read-only repository structural census. |
| [`scripts/scan/plan.py`](scripts/scan/plan.py) | `scan` | Read-only planning-artifact census/extraction of candidate modal/numeric/TODO evidence. |
| [`scripts/scan/tooling.py`](scripts/scan/tooling.py) | `scan` | Read-only target tooling/environment inventory without executing candidate tools. |
| [`scripts/selftest/assurance.py`](scripts/selftest/assurance.py) | `selftest` | Selftest/regression harness for `assurance` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/blocker_convergence.py`](scripts/selftest/blocker_convergence.py) | `selftest` | Selftest/regression harness for `blocker-convergence` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/cache_aware.py`](scripts/selftest/cache_aware.py) | `selftest` | Selftest/regression harness for `cache-aware` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/cognitive_faults.py`](scripts/selftest/cognitive_faults.py) | `selftest` | Selftest/regression harness for `cognitive-faults` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/cognitive_security.py`](scripts/selftest/cognitive_security.py) | `selftest` | Selftest/regression harness for `cognitive-security` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/concurrency.py`](scripts/selftest/concurrency.py) | `selftest` | Selftest/regression harness for `concurrency` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/context_representation.py`](scripts/selftest/context_representation.py) | `selftest` | Selftest/regression harness for `context-representation` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/emergency_cognitive.py`](scripts/selftest/emergency_cognitive.py) | `selftest` | Selftest/regression harness for `emergency-cognitive` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/emergency_repository.py`](scripts/selftest/emergency_repository.py) | `selftest` | Selftest/regression harness for `emergency-repository` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/fastpath.py`](scripts/selftest/fastpath.py) | `selftest` | Selftest/regression harness for `fastpath` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/memory.py`](scripts/selftest/memory.py) | `selftest` | Selftest/regression harness for `memory` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/model_adapter.py`](scripts/selftest/model_adapter.py) | `selftest` | Selftest/regression harness for `model-adapter` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/progress_liveness.py`](scripts/selftest/progress_liveness.py) | `selftest` | Selftest/regression harness for `progress-liveness` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/read_comparison.py`](scripts/selftest/read_comparison.py) | `selftest` | Selftest/regression harness for `read-comparison` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/read_reviewers.py`](scripts/selftest/read_reviewers.py) | `selftest` | Selftest/regression harness for `read-reviewers` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/read_substrate.py`](scripts/selftest/read_substrate.py) | `selftest` | Selftest/regression harness for `read-substrate` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/read_v2.py`](scripts/selftest/read_v2.py) | `selftest` | Selftest/regression harness for `read-v2` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/read_v2_reviewers.py`](scripts/selftest/read_v2_reviewers.py) | `selftest` | Selftest/regression harness for `read-v2-reviewers` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/run.py`](scripts/selftest/run.py) | `selftest` | Selftest/regression harness for `run` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/runtime_resume.py`](scripts/selftest/runtime_resume.py) | `selftest` | Selftest/regression harness for `runtime-resume` behavior using populated or adversarial fixtures. |
| [`scripts/selftest/session_epoch.py`](scripts/selftest/session_epoch.py) | `selftest` | Selftest/regression harness for `session-epoch` behavior using populated or adversarial fixtures. |
| [`scripts/skill/core.py`](scripts/skill/core.py) | `skill` | Skill ledger validation/operations. |
| [`scripts/state/lock.py`](scripts/state/lock.py) | `state` | Cooperative local lease/lock/fencing primitive; not an OS security boundary. |
| [`scripts/state/migrate.py`](scripts/state/migrate.py) | `state` | Dry-run-by-default state schema migration; `--apply` is mutating. |
| [`scripts/structural/core.py`](scripts/structural/core.py) | `structural` | Structural-candidate validation/operations. |
| [`scripts/verify/all.py`](scripts/verify/all.py) | `verify` | Aggregate runner for all 63 registered checks in isolated child interpreters. |
| [`scripts/verify/ambiguity.py`](scripts/verify/ambiguity.py) | `verify` | Verifier for `ambiguity` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/attestation.py`](scripts/verify/attestation.py) | `verify` | Verifier for `attestation` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/bounded_emergency.py`](scripts/verify/bounded_emergency.py) | `verify` | Verifier for `bounded-emergency` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/claims.py`](scripts/verify/claims.py) | `verify` | Verifier for `claims` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/cli.py`](scripts/verify/cli.py) | `verify` | Verifier for `cli` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/cognitive_invariants.py`](scripts/verify/cognitive_invariants.py) | `verify` | Verifier for `cognitive-invariants` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/compliance.py`](scripts/verify/compliance.py) | `verify` | Verifier for `compliance` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/context_representation.py`](scripts/verify/context_representation.py) | `verify` | Verifier for `context-representation` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/counts.py`](scripts/verify/counts.py) | `verify` | Verifier for `counts` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/discipline.py`](scripts/verify/discipline.py) | `verify` | Verifier for `discipline` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/emergency.py`](scripts/verify/emergency.py) | `verify` | Verifier for `emergency` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/enforcement.py`](scripts/verify/enforcement.py) | `verify` | Verifier for `enforcement` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/excludes.py`](scripts/verify/excludes.py) | `verify` | Verifier for `excludes` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/fastpath.py`](scripts/verify/fastpath.py) | `verify` | Verifier for `fastpath` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/golden.py`](scripts/verify/golden.py) | `verify` | Verifier for `golden` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/hygiene.py`](scripts/verify/hygiene.py) | `verify` | Verifier for `hygiene` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/index_scope.py`](scripts/verify/index_scope.py) | `verify` | Verifier for `index-scope` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/links.py`](scripts/verify/links.py) | `verify` | Verifier for `links` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/paths.py`](scripts/verify/paths.py) | `verify` | Verifier for `paths` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/placeholders.py`](scripts/verify/placeholders.py) | `verify` | Verifier for `placeholders` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/prefix.py`](scripts/verify/prefix.py) | `verify` | Verifier for `prefix` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/preserve.py`](scripts/verify/preserve.py) | `verify` | Verifier for `preserve` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/progress_liveness.py`](scripts/verify/progress_liveness.py) | `verify` | Verifier for `progress-liveness` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/provenance.py`](scripts/verify/provenance.py) | `verify` | Verifier for `provenance` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/read_contract.py`](scripts/verify/read_contract.py) | `verify` | Verifier for `read-contract` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/recall.py`](scripts/verify/recall.py) | `verify` | Verifier for `recall` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/release_identity.py`](scripts/verify/release_identity.py) | `verify` | Verifier for `release-identity` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/routes.py`](scripts/verify/routes.py) | `verify` | Verifier for `routes` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/runtime_resume.py`](scripts/verify/runtime_resume.py) | `verify` | Verifier for `runtime-resume` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/verify/width.py`](scripts/verify/width.py) | `verify` | Verifier for `width` contract/invariant; participates in the fail-closed verification surface where registered. |
| [`scripts/wiki/build.py`](scripts/wiki/build.py) | `wiki` | Derived Wiki build/validation surface. |

## v1.0.1-v1.0.2 script additions

| Script | Family | Public role |
| --- | --- | --- |
| [`scripts/convergence/watch.py`](scripts/convergence/watch.py) | `convergence` | Workflow-convergence semantic-frontier watcher/classifier surface. |
| [`scripts/handoff/terminal_reconcile.py`](scripts/handoff/terminal_reconcile.py) | `handoff` | Operator-facing cross-plane terminal reconciliation and successor-admission gate. |
| [`scripts/lib/c2convergence.py`](scripts/lib/c2convergence.py) | `lib` | Shared workflow-convergence classifier/policy helper; does not grant repository authority. |
| [`scripts/lib/c2terminal.py`](scripts/lib/c2terminal.py) | `lib` | Shared terminal truth and evidence-bound successor-admission helper; refusal authority only. |
| [`scripts/selftest/terminal_reconciliation.py`](scripts/selftest/terminal_reconciliation.py) | `selftest` | Populated/adversarial regression for terminal truth, successor admission, and claim reuse. |
| [`scripts/selftest/workflow_convergence.py`](scripts/selftest/workflow_convergence.py) | `selftest` | Directed, finite-state, and deterministic-fuzz workflow-convergence regression. |
| [`scripts/verify/terminal_reconciliation.py`](scripts/verify/terminal_reconciliation.py) | `verify` | Static/integration verifier for terminal reconciliation surfaces and resume wiring. |
| [`scripts/verify/workflow_convergence.py`](scripts/verify/workflow_convergence.py) | `verify` | Static/integration verifier for Workflow Convergence surfaces. |

## Aggregate verifier topology

[`scripts/verify/all.py`](scripts/verify/all.py) registers 63 check invocations. It runs ordinary validators and
selftests in isolated child interpreters; the assurance selftest is split into four independent chunks. The aggregate
fails if any registered check fails. A separate strict-vacuous mode can also fail when a check inspected an empty
corpus.

Registered check entrypoints/invocations are:

* `scripts/verify/counts.py`
* `scripts/verify/fastpath.py`
* `scripts/verify/progress_liveness.py`
* `scripts/verify/claims.py`
* `scripts/verify/paths.py`
* `scripts/verify/index_scope.py`
* `scripts/verify/links.py`
* `scripts/verify/excludes.py`
* `scripts/verify/width.py`
* `scripts/verify/hygiene.py`
* `scripts/verify/cli.py`
* `scripts/verify/provenance.py`
* `scripts/verify/compliance.py`
* `scripts/verify/preserve.py`
* `scripts/verify/placeholders.py`
* `scripts/jsonl/validate.py`
* `scripts/graph/validate.py`
* `scripts/handoff/validate.py`
* `scripts/goal/gate.py`
* `scripts/lessons/decay.py`
* `scripts/verify/recall.py`
* `scripts/verify/discipline.py`
* `scripts/verify/enforcement.py`
* `scripts/verify/routes.py`
* `scripts/verify/prefix.py`
* `scripts/verify/golden.py`
* `scripts/verify/ambiguity.py`
* `scripts/verify/runtime_resume.py`
* `scripts/verify/read_contract.py`
* `scripts/verify/context_representation.py`
* `scripts/verify/release_identity.py`
* `scripts/verify/emergency.py`
* `scripts/verify/bounded_emergency.py`
* `scripts/memory/core.py`
* `scripts/skill/core.py`
* `scripts/structural/core.py`
* `scripts/wiki/build.py`
* `scripts/verify/attestation.py`
* `scripts/verify/cognitive_invariants.py`
* `scripts/selftest/memory.py`
* `scripts/selftest/fastpath.py`
* `scripts/selftest/progress_liveness.py`
* `scripts/selftest/assurance.py`
* `scripts/selftest/assurance.py`
* `scripts/selftest/assurance.py`
* `scripts/selftest/assurance.py`
* `scripts/selftest/concurrency.py`
* `scripts/selftest/cognitive_security.py`
* `scripts/selftest/session_epoch.py`
* `scripts/selftest/model_adapter.py`
* `scripts/selftest/context_representation.py`
* `scripts/selftest/cache_aware.py`
* `scripts/selftest/cognitive_faults.py`
* `scripts/selftest/emergency_repository.py`
* `scripts/selftest/blocker_convergence.py`
* `scripts/selftest/runtime_resume.py`
* `scripts/selftest/read_substrate.py`
* `scripts/selftest/read_v2.py`
* `scripts/verify/workflow_convergence.py`
* `scripts/verify/terminal_reconciliation.py`
* `scripts/selftest/workflow_convergence.py`
* `scripts/selftest/terminal_reconciliation.py`
* `scripts/selftest/run.py`

The list contains repeated assurance invocations for distinct chunks; therefore invocation count and unique script
count are intentionally different.

For the v1.0.2 release freeze, the aggregate wrapper exhibited an orchestration timeout in this sandbox. The same 63 registered invocations were therefore executed serially in fresh child processes; all 63 passed per edition. The interrupted wrapper itself is not counted as PASS or repository FAIL.

## Pre-authority execution boundary

The shipped script documentation permits only a narrow set of distribution-owned target-read-only entry tools while
rollback authority is still pending: `scripts/scan/tooling.py`, `scripts/scan/census.py`, `scripts/scan/plan.py`, and
`scripts/install/preflight.py` in its default inspection modes. This is not blanket permission to run arbitrary
`scripts/`, project binaries, package managers, or candidate tools.

## Verification claim boundary

A passing validator proves only the contract it actually checks. A selftest is regression evidence, not proof of
all production environments. Synthetic adapter simulations are not live provider traffic. Empty-corpus/vacuous
success is explicitly distinguished from populated-runtime evidence.

See [Evidence, Provenance and Assurance Guide](C2COGNITIVE-EVIDENCE-PROVENANCE-ASSURANCE-GUIDE.md) and
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md).
