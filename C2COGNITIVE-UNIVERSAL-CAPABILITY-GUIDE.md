# C2Cognitive | Universal Capability Routing

**Version:** 1.1.19 (publication candidate)  
**Author:** Hafizh Al-Banna  
**Document class:** Public feature and process guide

> Explanatory documentation, not an execution authority or test report. Current `AGENTS.md`, active Goal, `.agent` contracts, host authorization and source code govern.

## What changes in the existing workflow

**Integration type:** Conditional planning extension.

**Existing path:** The operator selects domain runbooks from the active Goal and relevant repository context. The old governance gates still decide whether any implementation can proceed.

**New trigger:** A Goal touches a specific application capability, an unfamiliar industry family, or a cross-module business process.

## End-to-end process

1. Read the admitted Goal, relevant requirements and current source. Identify actual behavior; do not infer it from an industry label.
2. Run the read-only selector with explicit `--capability`, `--family`, `--module` or `--archetype` arguments. `--summary` offers bounded discovery.
3. The selector validates exact identifiers, closes declared dependencies and returns a finite list of runbook paths.
4. Read only selected runbooks and confirm each inferred dependency against the real project and its owners.
5. Bind chosen capabilities to actors, tenants, transitions, independent oracles, negative cases and project policy.
6. Forward those obligations to the existing Goal, exact-write planning and application assurance gates; never treat a selector result as authority.

### Decision / stop / recovery

A selection can be `ADVISORY_ONLY` and `BLOCKED_PENDING_PROJECT_EVIDENCE`; no product edit, execution success or compliance claim follows from it.

## Process diagram

```text
Goal + actual requirements
        |
  explicit capability ID
        |
  read-only selector
        |
  ID valid? -- no --> REJECT
        | yes
  bounded dependency closure
        |
  selected runbooks (ADVISORY_ONLY)
        |
  project evidence present? -- no --> BLOCKED
        | yes
  old exact-write/QA gates
```

## Does it change the previous process structure?

Adds an on-demand route before scoped planning. It does not replace `AGENTS.md`, change the Core rules or make all 58 families / 19 universal contracts mandatory.

| Boundary | Effect |
|---|---|
| `Active Goal` | Remains the source of authorized work; never generated from a guide. |
| `CORE / AGENTS.md` | Existing invariants and scoped routing remain higher authority. |
| `Exact write set` | Still required before actual product/repository mutation. |
| `Approvals and rollback` | Remain independent requirements for sensitive writes. |
| `Unselected feature` | Does not automatically add active work or global coverage. |
| `Verification` | Can strengthen a relevant acceptance gate; no synthetic result replaces real execution. |

## Illustrative scenario

Example: a custom appointment service chooses `scheduling-capacity` and `temporal-effective-backdate` only when its requirements contain those behaviors; it does not inherit HRIS or ERP legal rules.

## Read-only / bounded entry example

```sh
python3 -B scripts/domain/universal.py --project-type custom --capability temporal-effective-backdate
```

Run only after inspecting the actual installed source and prerequisites. Angle-bracket inputs are placeholders, not executable values.

## Implementation references in the distribution

- `.agent/runbooks/application-domain-router.md`
- `docs/UNIVERSAL-CAPABILITY-PROTOCOL.md`
- `scripts/domain/universal.py`
- `.agent/capability-registry.json`

## Boundaries and failure behavior

- `Unknown` is not `false`; unmet applicable obligations remain blockers.
- A guide cannot authenticate approvals or establish provider availability.
- Do not call a synthetic fixture a production app test.
- Stop or suspend with a named blocker if prerequisites, scope, evidence or resource budget are missing.
- Treat historical version notes and release evidence as provenance, not current compatibility proof.

## Existing docs to read next

- [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md)
- [C2COGNITIVE-REFERENCE.md](C2COGNITIVE-REFERENCE.md)
