# C2Cognitive | Bounded Resource and Temporary Workspace Controls

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Execution safety wrapper.

**Existing path:** Existing tool execution and QA jobs operate under declared budgets; an unbounded repository clone or orphaned subprocess can exhaust resources even if business logic passes.

**New trigger:** A scanner, audit, snapshot, regression, fixture copy or long-running command creates temporary files or child processes.

## End-to-end process

1. Resolve an exact file allowlist and bounded estimated bytes/files; do not recursively copy the adopted project root.
2. Check temporary destination and relevant storage class. Do not silently select a RAM filesystem such as `/dev/shm`.
3. Allocate only an owned workspace, execute with process timeout, memory and output caps and a declared cleanup owner.
4. Stop the affected lane when byte, file, output, time or process limits are hit; report the unfinished work as NOT-RUN.
5. On ordinary exit or exception clean exactly owned resources; do not broadly delete host temporary folders.
6. Re-run bounded tests and inspect residue before declaring the local resource gate complete.

### Decision / stop / recovery

Linux/WSL resource-gate runner reports unsupported on native Windows instead of claiming an unbounded PASS.

## Process diagram

```text
Explicit target paths + budgets
        |
  sparse allowlist / storage preflight
        |
  owned temporary workspace
        |
  bounded process + output + timeout
        |
  cap exceeded? -- yes --> suspend / NOT-RUN
        | no                         |
  verify actual result            owned cleanup
        |                         /
  owned cleanup + residue check --+
```

## Does it change the previous process structure?

Wraps auxiliary execution and QA. It does not rewrite the product workflow or permit cleanup of unowned data.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a test needs three source files, but a fixture script attempts to copy the entire monorepo. The allowlist preflight rejects this rather than consuming disk.

## Read-only / bounded entry example

```sh
python3 -B scripts/quality/run_resource_gates.py --iterations 200
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `scripts/lib/temp_safety.py`
- `.agent/runbooks/temp-workspace-safety.md`
- `scripts/quality/run_resource_gates.py`
- `scripts/quality/performance_budget.py`
- `docs/RESOURCE-CONTINUITY-HARDENING.md`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
