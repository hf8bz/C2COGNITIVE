# C2Cognitive Safe GATE 0 & Rollback Preflight Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain how early repository discovery remains mutation-free, why candidate tool execution is deferred, and how
rollback evidence is collected without prematurely claiming final write authority.

### Canonical implementation sources

- [SCAN-AND-ADOPT.prompt.md](SCAN-AND-ADOPT.prompt.md)
- [system-inventory.md](.agent/runbooks/system-inventory.md)
- [07-system-inventory.md](.agent/runbooks/system-inventory.md)
- [18-scan-automation.md](scripts/scan/)
- [config.yml](.agent/config.yml)

---

## GATE 0 principle

Early discovery is static. The repository may contain package managers, generators, runners, hooks, scripts, or
commands whose `--help`/`--version` invocation can still create caches, fetch dependencies, alter lockfiles, execute
project code, or touch user state.

Therefore availability is not permission to execute.

## Static evidence first

GATE 0 may inspect declared files, executable paths, configuration, CI, scripts, manifests, editor/agent
configuration, and known call sites using the trusted mutation-free subset. It should record claim limits when a tool
is only declared or unverified.

The current configuration explicitly keeps candidate-tool execution, discovery cache writes, and manifest writes
disabled at GATE 0.

## Rollback preflight

Early rollback inspection answers only questions such as:

- is there an independent recovery source for pristine C2Cognitive-owned files?
- are some planned operations create-only?
- does the selected source overlap the target and therefore fail as an independent before-image?
- are there unsafe paths?

It does not authorize a future unknown write.

## Source=target caveat

Comparing a repository directory to itself can make every file appear "identical" while proving nothing about an
independent before-image. Treat source overlap as a limitation of rollback evidence, not as manufactured proof.

## When execution can happen

Candidate tool execution occurs only after the workflow has enough evidence/authority to justify it under the selected
entry mode and runbook. If the tool is not required for the next safe action, keep the claim limited rather than
widening execution.

## Relation to exact write planning

Final rollback authority is computed after the exact byte-changing write set is known. See
[C2COGNITIVE-ACTUAL-WRITE-PLAN-ROLLBACK-GUIDE.md](C2COGNITIVE-ACTUAL-WRITE-PLAN-ROLLBACK-GUIDE.md).

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
