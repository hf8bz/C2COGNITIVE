# C2Cognitive Actual Write Plan & Rollback Authority Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Describe the mutation boundary used by C2Cognitive adoption and controlled repository work: semantic scope, the
exact byte-changing write set, fresh pre-state, and path-scoped rollback authority must be separated before a
write is considered authorized.

### Canonical implementation sources

- [SCAN-AND-ADOPT.prompt.md](SCAN-AND-ADOPT.prompt.md)
- [INSTALL-WORKFLOW-ONLY.prompt.md](INSTALL-WORKFLOW-ONLY.prompt.md)
- [blocker-handling.md](.agent/runbooks/blocker-handling.md)
- [context-compaction.md](.agent/runbooks/context-compaction.md)
- [bounded-emergency-authority.schema.md](.agent/bounded-emergency-authority.schema.md)

---

## Four concepts that must stay separate

### 1. Semantic scope

Semantic scope answers **whether C2Cognitive is allowed to change a path at all** in the selected entry mode and
active Goal. A path can be technically reversible and still be forbidden.

### 2. `ACTUAL_WRITE_SET`

The exact operations that will change target bytes:

```text
CREATE <path>
MODIFY <path>
DELETE <path>
```

A candidate whose final desired bytes already equal current bytes is a no-op and should not be authorized as a
mutation.

### 3. Fresh expected pre-state

Before a write, the authority must still correspond to the bytes/state that were inspected. A stale plan is not
rescued by having once been valid.

### 4. Rollback authority

Rollback authority is proven for the exact planned path/action. A backup for one file does not authorize another file;
an independent distribution can restore pristine control-plane files only where that recovery basis actually applies.

## Canonical ordering

```text
select entry mode + active Goal constraints
                 v
resolve semantic decisions
                 v
materialize exact byte-changing write plan
                 v
prove path-scoped rollback basis
                 v
refresh expected pre-state
                 v
authorize exact action + target
                 v
write
                 v
verify outcome
```

Rollback never widens semantic scope. A `WORKFLOW_ONLY` run cannot modify product code merely because restoring it
would be easy.

## Pending audit state is not automatically a blocker

C2Cognitive distinguishes logical information from permission to persist that information into the target repository.
During early read-only phases, a decision, failure, discovery, discipline event, or handoff can remain pending
session/host evidence until write authority exists. The run must not mutate the repository merely to create the
artifact that would later justify mutation.

## Emergency writes

Bounded Emergency Authority (BEA) can overlay an already exact repository-write plan. It is not wildcard permission.
Cognitive Emergency Authorization (CEA) is a different authority plane and does not grant repository writes. See
[C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE.md](C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE.md).

## Review checklist

Before a target write, answer all of these independently:

- Is the path inside the selected entry mode?
- Is the action required by the active Goal or explicit workflow-only scope?
- Will bytes actually change?
- Is action + target exact?
- Is the pre-state fresh?
- Is rollback proven for this exact operation?
- Does any human decision remain unresolved?
- Does emergency authority, if used, match this exact operation and remain valid?
- Will verification measure the intended outcome rather than only process success?

## What this guide does not claim

A rollback plan does not guarantee recovery from every external system effect, distributed side effect,
package-registry action, mobile distribution, or irreversible third-party transaction. Those require domain-specific
controls in the matching runbook/scope.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
