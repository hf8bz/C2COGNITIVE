# C2Cognitive v1.0.0 Reference

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Provide a compact public lookup surface for the stable concepts, paths, entry modes, cognitive objects, authority
boundaries, and verification entry points shipped in C2Cognitive v1.0.0.

### Canonical implementation sources

- [AGENTS.md](AGENTS.md)
- [config.yml](.agent/config.yml)
- [rule-registry.md](.agent/rule-registry.md)
- [counts.generated.json](.agent/counts.generated.json)
- [START-HERE.md](START-HERE.md)

---

## Release identity

| Field | Value |
| --- | --- |
| Product | C2Cognitive Core |
| Public version | `1.0.0` |
| Release | Release 1 |
| Release date | 30 August 2026 |
| Author | Hafizh Al-Banna |
| License | MIT |
| Bundled adapter | C2ModelAdapter `0.5.5` |

## Entry modes

| Mode | Repository | Product writes |
| --- | --- | --- |
| `ADOPT_WITH_GOAL` | existing | gated by active Goal + exact authority |
| `WORKFLOW_ONLY` | existing | forbidden |
| `BOOTSTRAP` | empty/new | gated after bootstrap planning |

## Cognitive objects

| Object | Role | Authority note |
| --- | --- | --- |
| L0 memory | significant observation/event | data, evidence-bounded |
| L1 memory | atomic evidence-backed fact | data, evidence-bounded |
| L2 memory | recurring scenario | requires multiple support anchors |
| L3 memory | stable project/team/operational/persona knowledge | repeated support; still not write authority |
| Skill | reusable procedural advice | verified lifecycle; advisory |
| structural candidate | source-bound structural observation | advisory, freshness-bound |
| Wiki generation | derived project view | projection, not canonical authority |
| Goal | durable objective/finish contract | does not authorize arbitrary writes |
| handoff/resume capsule | continuation state | not mutation authority |

## Authority separation

```text
knowledge          != authority
Goal               != arbitrary write permission
rollback capability!= semantic scope
CEA                != BEA
cache hit          != evidence
ACRP               != evidence selection
liveness finding   != write row
```

## Key paths

| Need | Path |
| --- | --- |
| core invariants/router | `AGENTS.md` |
| configuration | `.agent/config.yml` |
| current runbooks | `.agent/runbooks/` |
| domain scopes | `.agent/scopes/` |
| memory | `.agent/memory/` |
| Skill | `.agent/skills/` |
| structural candidates | `.agent/structural/` |
| Wiki | `.agent/wiki/` |
| Goals | `.agent/goals/` |
| runs/state | `.agent/runs/`, `.agent/state/` |
| graph schemas | `.agent/graph/schema/` |
| public docs | `C2COGNITIVE-*.md` |
| adapter | `adapter/C2ModelAdapter-v0.5.5/` |
| verification | `scripts/verify/` |
| selftests | `scripts/selftest/` |

## C2PY

```text
POSIX:   /bin/sh scripts/c2python.sh <script> [args]
Windows: scripts\c2python.cmd <script> [args]
```

Minimum Python runtime enforced by the launcher: 3.8.

## Verification entry points

```text
<C2PY> scripts/verify/counts.py
<C2PY> scripts/verify/links.py
<C2PY> scripts/verify/release_identity.py
<C2PY> scripts/verify/all.py
```

The aggregate suite can include nontrivial finite/selftest work. Do not report its PASS until the process actually
exits successfully.

## Core distribution counts

`.agent/counts.generated.json` and `scripts/verify/counts.py` are the source of published template counts. The
executable distribution manifest remains separate from public documentation added at repository root; adding
explanatory public docs does not silently redefine the control-plane file manifest.

## Public documentation

Use [C2COGNITIVE-DOCS-START-HERE.md](C2COGNITIVE-DOCS-START-HERE.md) for the complete map.

---

## Exhaustive public references

The compact reference above is supplemented by exhaustive catalogs:

* [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md) - all 39 Core rules plus scope/router surfaces;
* [Configuration Reference](C2COGNITIVE-CONFIGURATION-REFERENCE.md) - all 306 config keys and 228 thresholds;
* [Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md) - all 41 runbook files (40 procedures + template);
* [Schema and Runtime State Catalog](C2COGNITIVE-SCHEMA-STATE-CATALOG.md) - `.agent` schemas/state/metadata;
* [Prompt Catalog](C2COGNITIVE-PROMPT-CATALOG.md) - 3 entry prompts + 13 staged/continuity prompts;
* [Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md) - all 95 Python files and aggregate verifier topology;
* [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md) - every non-internal shipped path.
