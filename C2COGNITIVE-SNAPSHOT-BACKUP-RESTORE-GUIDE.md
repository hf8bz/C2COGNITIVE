# C2Cognitive | Allowlisted Snapshot, Verification and Restore

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Artifact lifecycle safety path.

**Existing path:** Named rollback remains mandatory for repository edits. A generic copy or ZIP, however, is not sufficient evidence that restore is safe or byte-identical.

**New trigger:** A local distribution snapshot, backup replay or bounded restore exercise is requested.

## End-to-end process

1. Select source files from `.agent/distribution-files.txt` and reject unsafe/duplicated/VCS-private paths or non-regular symlinked inputs.
2. Read bounded source metadata and pack exact file content, SHA-256 and approved normal file modes.
3. Verify the archive namespace, member size, manifest, digest and modes before any restore.
4. Restore to a *new*, nonexistent destination via staging, with content hash checks and file/directory sync.
5. Publish without overwriting the destination. If final directory durability cannot be confirmed, mark INDETERMINATE and inspect before retry.
6. Compare all selected source bytes against restored bytes. Preserve separate transaction-specific rollback authority for product modifications.

### Decision / stop / recovery

`pack`, `verify`, and `restore` are distinct. Restoring an archive does not authorize editing a live repository; overwrite of existing destination is intentionally rejected.

## Process diagram

```text
Distribution allowlist
        |
  pack regular files + hashes + modes
        |
  verify path/size/digest/mode
        |
  valid? -- no --> FAIL / reject
        | yes
  stage to new destination only
        |
  fsync + no-replace publish
        |
  durable? -- unknown --> INDETERMINATE / inspect
        | yes
  compare source and restored bytes
```

## Does it change the previous process structure?

Introduces safer local package/restore mechanics beside existing change rollback, not a substitute for DB backup or production disaster recovery.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: an archive passes ZIP CRC but fails member SHA-256 or has a symlink path. Restore stops before destination publication.

## Read-only / bounded entry example

```sh
python3 -B scripts/quality/repository_snapshot.py verify --archive <snapshot.zip>
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `scripts/quality/repository_snapshot.py`
- `scripts/quality/run_resource_gates.py`
- `.agent/distribution-files.txt`
- `.agent/runbooks/backup-restore.md`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
