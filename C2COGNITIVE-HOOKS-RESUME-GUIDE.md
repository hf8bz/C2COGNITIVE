# C2Cognitive | Compaction Hooks and Resume Boundaries

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Optional host adapter and continuity guard.

**Existing path:** The established Goal, HANDOFF/CURSOR and terminal reconciliation preserve long-running state. Hook events are not themselves a source of repository authority.

**New trigger:** A verified host supports compaction/session events or a manual checkpoint is requested.

## End-to-end process

1. Check installed host/version/event contract and exact configuration; do not assume a file sitting on disk is activated.
2. Choose only the matching bridge. OpenCode V1 and V2 adapters must not be loaded together.
3. During authorized work, preserve bounded Goal, HANDOFF/CURSOR, blockers, evidence pointers and approvals; no surprise writes from the hook.
4. On event delivery, the bridge reads bounded exact state and emits advisory text, or a degraded notice if state is missing/unsafe.
5. After compact/restart, run normal rehydration, verify current source and terminal truth. Reject stale cursor reopening a completed run.
6. When native event delivery is unverified, take a manual checkpoint; new sessions inherit existing Goal and cannot mint write authorization.

### Decision / stop / recovery

A hook can advise, but not independently auto-compact, persist an unauthorized handoff, grant a new Goal or resume a terminal run.

## Process diagram

```text
Verified harness config + compatible adapter
        |
  native event observed? -- no --> manual checkpoint
        | yes                             |
  bounded advisory output               |
        |                                |
  canonical HANDOFF / CURSOR rehydrate <-+
        |
  terminal truth? -- COMPLETED --> no same-run resume
        | active
  revalidate Goal/source/approval before action
```

## Does it change the previous process structure?

Adds optional host integration around the established continuity workflow. The canonical state machine and write authority remain unchanged.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: the host emits a compaction event after plugin reload. The bridge emits a bounded continuity notice; the agent still revalidates HANDOFF and source before writing.

## Read-only / bounded entry example

```sh
python3 -B scripts/hooks/continuity.py --harness manual
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `.agent/runbooks/harness-hooks.md`
- `scripts/hooks/README.md`
- `scripts/hooks/continuity.py`
- `scripts/hooks/opencode.mjs`
- `scripts/hooks/opencode-v2.mjs`
- `scripts/handoff/terminal_reconcile.py`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
