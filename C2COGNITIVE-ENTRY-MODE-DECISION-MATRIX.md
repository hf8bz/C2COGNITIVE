# C2Cognitive Entry Mode Decision Matrix

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Choose the correct adoption path before running a prompt. C2Cognitive has distinct handling for an existing
repository with implementation intent, an existing repository needing only the control plane, and a new/empty
repository.

### Canonical implementation sources

- [START-HERE.md](START-HERE.md)
- [SCAN-AND-ADOPT.prompt.md](SCAN-AND-ADOPT.prompt.md)
- [INSTALL-WORKFLOW-ONLY.prompt.md](INSTALL-WORKFLOW-ONLY.prompt.md)
- [BOOTSTRAP-NEW-REPO.prompt.md](BOOTSTRAP-NEW-REPO.prompt.md)

---

## Decision table

| Repository state / intent | Entry mode | Start file | Goal behavior | Product mutation |
| --- | --- | --- | --- | --- |
| Existing repo; adoption continues toward implementation | `ADOPT_WITH_GOAL` | `SCAN-AND-ADOPT.prompt.md` | PHASE 8 may emit a Goal after readiness | only after Goal + exact write authority |
| Existing repo; install/repair C2Cognitive control plane only | `WORKFLOW_ONLY` | `INSTALL-WORKFLOW-ONLY.prompt.md` | preserves prior goal state; emits no new Goal | forbidden |
| Empty / brand-new repo | `BOOTSTRAP` | `BOOTSTRAP-NEW-REPO.prompt.md` | planning/bootstrap path can emit a Goal after readiness | gated after bootstrap planning |

## Decision flow

```text
Is the repository empty / brand-new?
  +- yes -> BOOTSTRAP
  +- no
       |
       +- Do you want only C2Cognitive workflow/control-plane install or repair?
       |      +- yes -> WORKFLOW_ONLY
       |      +- no  -> ADOPT_WITH_GOAL
       |
       +- Product implementation requires an active admitted Goal before product writes.
```

## Important edge cases

### No active Goal in an existing repository

This does **not** automatically imply `WORKFLOW_ONLY`. Use workflow-only only when the requested semantic scope is
control-plane installation/repair. If the intent is product implementation, the run must converge on a Goal rather
than silently changing entry mode.

### Existing C2Cognitive installation

Use the same decision based on semantic intent. A workflow-only repair can update/repair the C2Cognitive-owned control
plane while preserving product behavior and Goal state.

### Empty repository with no planning material

BOOTSTRAP can require a bounded interview/decision process. Do not invent requirements merely to make the bootstrap
look complete.

## GATE 0

All entry modes begin with conservative discovery. Candidate tools are not automatically executed merely because they
are installed or have `--help`/`--version` interfaces. See
[C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md](C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md).

## Rule of thumb

Choose entry mode from **repository condition + requested semantic intent**, never from convenience.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
