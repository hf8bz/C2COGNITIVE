# C2Cognitive v1.0.0 File Map

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Map the repository into public documentation, executable control-plane distribution, runtime state, verification
tooling, and the bundled model adapter.

### Canonical implementation sources

- [distribution-files.txt](.agent/distribution-files.txt)
- [runtime-artifacts.txt](.agent/runtime-artifacts.txt)
- [counts.generated.json](.agent/counts.generated.json)

---

## Repository layers

```text
C2Cognitive/
+-- README.md                         public GitHub landing page
+-- C2COGNITIVE-*.md                 public explanatory documentation
+-- START-HERE.md                    executable-package entry orientation
+-- SCAN-AND-ADOPT.prompt.md         existing repo + Goal-emitting adoption
+-- INSTALL-WORKFLOW-ONLY.prompt.md  existing repo + control-plane only
+-- BOOTSTRAP-NEW-REPO.prompt.md     new/empty repo bootstrap
+-- AGENTS.md                        core invariants + routing
+-- .agent/                          canonical control-plane contracts/state paths
+-- prompts/                         staged cognitive/workflow prompts
+-- eval/                            retrieval/rubric evaluation assets
+-- scripts/                         scanners, validators, selftests, lifecycle tools
+-- adapter/C2ModelAdapter-v0.5.5/   bundled host-side model adapter
+-- CHANGELOG.md
+-- CHECKLIST.md
+-- PLACEHOLDERS.md
+-- CONTRIBUTING.md
+-- SECURITY.md
+-- LICENSE
+-- VERSION
```

## Public root documentation

The repository carries a root-level public documentation surface with 24 C2Cognitive-specific Markdown files. These
files explain the system and link into canonical implementation sources. They are deliberately not used to manufacture
a new authority plane.

## `.agent/`

Major areas include:

- `config.yml`  -  centralized operational configuration/thresholds;
- `rule-registry.md`  -  stable rule identifiers and change state;
- `distribution-files.txt`  -  executable/control-plane distribution manifest;
- `runtime-artifacts.txt`  -  paths expected to be created/updated at runtime;
- `runbooks/`  -  concrete operational procedures;
- `scopes/`  -  lane/domain-specific rules;
- `memory/`  -  L0-L3 streams and schema;
- `skills/`  -  verified Skill lifecycle surface;
- `structural/`  -  source-bound structural candidates;
- `wiki/`  -  derived Wiki graph/generation state;
- `graph/schema/`  -  typed graph schema/example;
- `goals/`, `runs/`, `state/`  -  durable execution/continuation planes;
- authority/provenance/model-adapter/progress schemas.

## `scripts/`

Key families:

```text
agent/       loadout, lease, representation, worker/session coordination
budget/      resource budget checks
emergency/   CEA/BEA proposal/effect logic
 goal/       Goal gate/lifecycle
 graph/      graph operations
 handoff/    continuation state
 install/    adoption/install preflight/materialization helpers
 interview/  bootstrap decision support
 jsonl/      bounded/governed JSONL utilities
 lessons/    lesson lifecycle
 memory/     L0-L3 memory lifecycle/security purge
 progress/   liveness/progress state
 provenance/ provenance export
 read/       BR-v2 bounded physical ingestion
 scan/       static/read-only discovery scanners
 selftest/   finite/integration selftests
 skill/      Skill lifecycle
 state/      governed state utilities
 structural/ structural candidate lifecycle
 verify/     registered verification checks
 wiki/       derived Wiki generation/publication
```

## Adapter

`adapter/C2ModelAdapter-v0.5.5/` is bundled in each language repo. It remains outside the
`.agent/distribution-files.txt` control-plane manifest because it is a host-side adapter component with its own
tests/simulation/lifecycle.

## Distribution manifest versus repository file count

The control-plane distribution manifest intentionally counts the C2Cognitive-owned executable/template corpus, not
every public explanatory file and not the separately bundled adapter. This distinction prevents a documentation
addition from silently changing the semantic meaning of the installer manifest.

For current measured counts, run:

```text
<C2PY> scripts/verify/counts.py
```

---

## Exhaustive file coverage

This file map is the human-oriented layer map. For a path-by-path audit of every non-internal shipped repository file,
see [C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md).

The current audited source package contains 286 files: 255 non-internal repo files plus 31 internal `docs/` files.
The public documentation package intentionally republishes no internal `docs/` files. The 255 non-internal files
are all assigned to public documentation owners, and all 31 internal-document topics are mapped to root public
replacements. The resulting documentation accounting is 286/286 source-file surfaces with zero unmapped functional
areas; this does not claim that the internal document bytes themselves are redistributed.

The main exhaustive catalogs are:

* [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md)
* [Configuration Reference](C2COGNITIVE-CONFIGURATION-REFERENCE.md)
* [Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md)
* [Schema and Runtime State Catalog](C2COGNITIVE-SCHEMA-STATE-CATALOG.md)
* [Prompt Catalog](C2COGNITIVE-PROMPT-CATALOG.md)
* [Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md)
