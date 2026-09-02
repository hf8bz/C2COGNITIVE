# C2Cognitive Install, Adopt and Bootstrap Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

This guide exposes the full repository-entry surface: existing-repo adoption, workflow-only installation, new-repo
bootstrap, static preflight, question handling, Goal readiness, and post-adoption continuity.

## Choose one of three entry modes

| Condition | Entry prompt | Result |
| --- | --- | --- |
| Existing repo, continue into implementation | `SCAN-AND-ADOPT.prompt.md` | adopt control plane, reconcile/inherit state, then emit/use a ready Goal |
| Existing repo, governance only | `INSTALL-WORKFLOW-ONLY.prompt.md` | install/repair C2Cognitive with zero product-behavior mutation and no synthetic maintenance Goal |
| Empty/new repo | `BOOTSTRAP-NEW-REPO.prompt.md` | derive initial authority/questions from planning artifacts, then bootstrap under Goal readiness |

## Pre-authority phase

Before rollback authority, execution is intentionally narrow. Static discovery and the shipped target-read-only
scanners/preflight can gather evidence, but project binaries, package managers, candidate tools, downloads, installs,
and target mutation are not implicitly authorized.

[`scripts/install/preflight.py`](scripts/install/preflight.py) distinguishes target, independent template/restore
basis, exact `create|modify|delete` plan operations, expected target pre-state, and per-action verification. Its
default inspection modes are not write permission.

## Tooling inventory

`scripts/scan/tooling.py` inventories what is statically knowable about tools and call sites without launching
candidate tools. Missing/unverified capabilities become claim limits and install offers rather than invented passes.

## Repository or planning census

Existing repositories use structural/tool/test/document census. New repositories use planning-artifact census.
`scripts/scan/plan.py` deliberately emits evidence candidates rather than manufacturing requirements from modal
sentences.

## Human decision queue

Ambiguous, destructive, or consequential decisions are staged into a bounded PHASE 3 queue. `scripts/interview/ask.py`
can emit the queue without writing answers; its authorized answer-writing mode is a mutation and therefore follows
the write contract.

## Goal behavior

`ADOPT_WITH_GOAL` and `BOOTSTRAP` require Goal readiness before product implementation. `WORKFLOW_ONLY` is the narrow
goal-free exception for control-plane installation/repair. Existing Goal state is preserved and inherited rather
than silently restarted or deleted.

## Continuity immediately after authority settles

Once PHASE 3 / exact write planning settles, C2Cognitive can create/refresh the portable resume capsule when its
own write contract permits. Budget/session suspension routes to Prompt 97; compaction routes to Prompt 98; durable
long-session resume uses Prompt 99.

## Adoption does not prove project correctness

Installing C2Cognitive establishes the control-plane structure and verification surfaces. It does not make target
requirements correct, create missing test coverage without approval, certify production, or prove every tool works
in the target environment.

See [Entry Mode Matrix](C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md),
[Prompt Catalog](C2COGNITIVE-PROMPT-CATALOG.md), and [Safe GATE 0 Guide](C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md).
