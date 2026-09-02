# C2Cognitive Blocker Convergence Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Prevent recoverable uncertainty or tooling limitations from being mislabeled as terminal blockers while still
failing closed when an actual authority, evidence, safety, or human-decision gate is red.

### Canonical implementation sources

- [blocker-handling.md](.agent/runbooks/blocker-handling.md)
- [system-inventory.md](.agent/runbooks/system-inventory.md)
- [preflight-recall.md](.agent/runbooks/preflight-recall.md)

---

## Blocker classes

C2Cognitive separates conditions that require different responses. The exact vocabulary is owned by the current
runbook/configuration, but operationally the distinction is:

| Condition | Typical response |
| --- | --- |
| missing but nonessential tool evidence | narrow the claim; continue safe work |
| approved tool is unavailable | use a safe fallback or record a tooling gap |
| semantic ambiguity with consequential outcomes | ask a bounded human question |
| exact write authority missing | stop the write; continue read-only work if safe |
| stale evidence/pre-state | refresh evidence |
| resource budget exhausted | suspend resumably; do not call it completion |
| security/secret incident | contain and follow incident authority |
| Goal conflict or forbidden action | stop/replan or require human decision |

## Convergence procedure

1. State the blocked action precisely.
2. Identify what evidence or authority is missing.
3. Classify whether the missing item is actually required for the next safe action.
4. Prefer narrowing the claim over inventing evidence.
5. Prefer an existing bounded fallback over widening tool execution.
6. If a human decision is consequential, persist one bounded question only through a currently authorized
   decision mechanism; otherwise keep it as pending host/session evidence.
7. Resume from the first safe unresolved action; do not restart completed discovery.

## What is not a blocker by itself

- A candidate tool was not executed at GATE 0.
- A documentation claim is unverified.
- A cache miss occurred.
- A graph index does not exist when bounded search/read is sufficient.
- A checkpoint cannot be persisted to the target while product work can safely remain read-only.
- An aggregate verifier is slow, provided no completion claim is made before it finishes.

## What must fail closed

Examples include missing exact write authority, unresolved consequential semantic contradiction, invalid emergency
grant, unsafe path containment, exposed sensitive text requiring containment, or evidence known to be stale where
freshness is a precondition.

## Definition of convergence

A blocker is converged when the run has one of four explicit states:

```text
RESOLVED
SAFE_FALLBACK_SELECTED
HUMAN_DECISION_REQUIRED
STOPPED_BY_REAL_GATE
```

Anything else is still ambiguous and should not be reported as completion.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
