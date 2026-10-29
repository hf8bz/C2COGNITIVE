# C2Cognitive | Guarded Version Migration and Workflow Continuity

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Separate distribution upgrade path.

**Existing path:** A human-authorized repository upgrade must preserve the adopted application and existing Goal. Merely replacing control files is not sufficient to preserve tailored rules.

**New trigger:** An operator chooses to move an installation from the exact previous public version to the frozen local source baseline.

## End-to-end process

1. Determine project edition, public baseline identity, exact distribution-path inventory and locally customized governance files.
2. Run the patch-specific read-only check first. Reject path/digest drift or unknown baselines rather than guessing a merge.
3. Separate product files, adopted custom changes and generated state from controlled template paths.
4. Obtain any required approval for exact modifications and prepare a named rollback; do not alter the active Goal or its completion state opportunistically.
5. Apply only the declared patch with its own documented applier in a disposable copy first, then verify exact target inventory and resume compatibility.
6. For altered custom files, perform deliberate three-way review rather than silently overwriting local user rules.

### Decision / stop / recovery

A local patch replay is not universal proof that an arbitrary live checkout matches its expected official public predecessor. Fail closed on non-identical assets.

## Process diagram

```text
Exact previous public source inventory
        |
  read-only digest/path preflight
        |
  mismatch? -- yes --> STOP / manual reconcile
        | no
  named rollback + exact authorized modifications
        |
  disposable patch replay + target verification
        |
  customized paths conflict? -- yes --> manual 3-way merge
        | no
  apply scoped upgrade / revalidate Goal and resume
```

## Does it change the previous process structure?

Changes the installed distribution only when explicitly initiated. It is not a new Goal, automatic migration, or live GitHub mutation.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a team changed `.agent/config.yml`. A strict public patch rejects or isolates the conflict; the operator must reconcile that config, not force overwrite.

## Implementation references in the distribution

- `INSTALL-WORKFLOW-ONLY.prompt.md`
- `START-HERE.md`
- `AGENTS.md`
- `.agent/distribution-files.txt`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
