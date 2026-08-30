# C2Cognitive Workflow-Only Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Describe the explicit `WORKFLOW_ONLY` entry mode for installing, repairing, or verifying the C2Cognitive control
plane in an existing repository without changing product behavior and without manufacturing a new Goal.

### Canonical implementation sources

- [INSTALL-WORKFLOW-ONLY.prompt.md](INSTALL-WORKFLOW-ONLY.prompt.md)
- [SCAN-AND-ADOPT.prompt.md](SCAN-AND-ADOPT.prompt.md)
- [START-HERE.md](START-HERE.md)
- [C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md](C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md)

---

## When to use

Use `WORKFLOW_ONLY` when the repository already exists and the requested semantic intent is limited to
C2Cognitive-owned governance/control-plane installation or repair.

Do **not** choose it simply because there is no active Goal.

## Hard semantic boundary

A valid workflow-only run may change only paths permitted by the workflow-only contract. Product
behavior/source/configuration outside that control-plane scope remains forbidden even if a rollback would be easy.

## Goal behavior

The wrapper sets `ENTRY_MODE=WORKFLOW_ONLY` and delegates the adoption gates. At finalization it preserves the meaning
of Goal state and emits no new Goal. An absent or terminal prior Goal is therefore valid for this mode.

## High-level flow

```text
existing repository
      v
INSTALL-WORKFLOW-ONLY.prompt.md
      v
set ENTRY_MODE=WORKFLOW_ONLY
      v
run shared scan/adoption gates
      v
resolve control-plane collisions/decisions
      v
materialize exact workflow-only write set
      v
rollback + freshness + verification
      v
preserve Goal state; emit no product Goal
```

## Stop conditions

Stop or switch mode if:

- the repository is empty/brand-new;
- requested work includes product/feature behavior;
- a required control-plane change lacks exact write/rollback authority;
- consequential semantic conflict requires a human decision;
- GATE 0 would require unsafe candidate-tool execution;
- or security/path containment fails.

## After installation

Product work later requires the normal Goal/write gates. Workflow-only completion is not product readiness.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
