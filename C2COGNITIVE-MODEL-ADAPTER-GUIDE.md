# C2Cognitive Model Adapter & Cache-Awareness Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain why C2ModelAdapter v0.5.5 is bundled with the release while remaining a host-side protocol/capability
boundary rather than becoming C2Cognitive repository authority.

### Canonical implementation sources

- [19-model-adapter-cache-awareness.md](.agent/runbooks/model-adapter.md)
- [model-adapter.schema.md](.agent/model-adapter.schema.md)
- [model-adapter.md](.agent/runbooks/model-adapter.md)
- [README.md](adapter/C2ModelAdapter-v0.5.5/README.md)
- [MODEL-COVERAGE.md](adapter/C2ModelAdapter-v0.5.5/MODEL-COVERAGE.md)

---

## Distribution versus authority

The release bundles:

```text
adapter/C2ModelAdapter-v0.5.5/
```

This makes the repository package self-contained for the adapter version that C2Cognitive expects. It does **not**
mean provider/runtime state is imported into the Core authority model.

The adapter remains host-side because model APIs differ in tool-call IDs, structured argument encoding, reasoning
state, streaming assembly, cache behavior, router aliases, failover semantics, and effective model identity.

## Effective route

A logical router/combo name is provenance. The effective physical model/provider route determines the runtime
capability contract. When failover changes family, provider-owned continuation IDs, reasoning state, or cache identity
must not be replayed as if the new provider owned them.

## Cache awareness

Cache is an optimization surface:

```text
cache hit  != correctness
cache hit  != evidence
cache hit  != freshness
cache hit  != write authority
cache hit  != completion
```

Stable-prefix or cache-scope information can help avoid accidental churn. Raw prompt prefixes, provider cache keys, KV
cache contents, credentials, and private reasoning state are not durable C2Cognitive authority.

## Capability admission

Unknown or merely similar model names should not be trusted by string resemblance alone. Capability admission should
be based on the verified adapter profile/contract. A watch/quarantine profile fails closed until the required
API/tool/cache contract is verified.

## Why the adapter is not a separate release requirement

For normal C2Cognitive users, a separate adapter ZIP would duplicate bytes already bundled in the language repository.
A separate adapter artifact is useful only when a maintainer intentionally manages the adapter lifecycle independently
or reuses it across another host/product.

## Verification

The adapter directory includes its own unit tests and deterministic simulation surfaces. Run its canonical
`run_selftest.py` from the adapter root so its expected `PYTHONPATH`/test sequence is applied.

## Boundary

Protocol compatibility does not prove that a model selected the semantically correct tool or produced a correct
answer. C2Cognitive still evaluates evidence, Goal, safety, and write authority above the adapter layer.

---


## Complete bundled adapter inventory

The 27-file adapter tree is accounted for below. This table documents packaging/role; implementation truth remains
in the adapter files and tests themselves.

| Adapter path | Role |
| --- | --- |
| [`CHANGELOG.md`](adapter/C2ModelAdapter-v0.5.5/CHANGELOG.md) | Adapter change history; current package remains v0.5.5. |
| [`MODEL-COVERAGE.md`](adapter/C2ModelAdapter-v0.5.5/MODEL-COVERAGE.md) | Admission-registry/profile coverage and lifecycle labels; not live-endpoint proof. |
| [`README.md`](adapter/C2ModelAdapter-v0.5.5/README.md) | Adapter architecture, route identity, failover portability, semantic response admission and verification. |
| [`c2modeladapter/__init__.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/__init__.py) | Public package exports. |
| [`c2modeladapter/base.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/base.py) | Core adapter base abstractions/common protocol foundation. |
| [`c2modeladapter/cache.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/cache.py) | Provider/runtime-scoped cache planning and cache identity helpers. |
| [`c2modeladapter/combo.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/combo.py) | Opaque heterogeneous-router combo portability and per-attempt request preparation. |
| [`c2modeladapter/effective_model.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/effective_model.py) | Effective-route resolution, bounded aliases, canonical model-family rebinding. |
| [`c2modeladapter/errors.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/errors.py) | Adapter error types/fail-closed signaling. |
| [`c2modeladapter/factory.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/factory.py) | Adapter/profile construction from admitted runtime identity. |
| [`c2modeladapter/failover.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/failover.py) | Cross-route failover transition planning and non-portable state handling. |
| [`c2modeladapter/open_weight.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/open_weight.py) | Open-weight model/profile compatibility support. |
| [`c2modeladapter/probe.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/probe.py) | Capability/probe evidence support. |
| [`c2modeladapter/providers.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/providers.py) | Provider/API-surface profile definitions and normalization. |
| [`c2modeladapter/registry.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/registry.py) | Model/provider/profile admission registry. |
| [`c2modeladapter/request_policy.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/request_policy.py) | Provider/runtime request-policy validation and normalization. |
| [`c2modeladapter/structured.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/structured.py) | Structured tool-call/response normalization and validation support. |
| [`c2modeladapter/transition.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/transition.py) | Model/provider/runtime transition rules. |
| [`c2modeladapter/types.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/types.py) | Canonical adapter data structures/type contracts. |
| [`c2modeladapter/validation.py`](adapter/C2ModelAdapter-v0.5.5/c2modeladapter/validation.py) | Semantic/protocol validation helpers. |
| [`pyproject.toml`](adapter/C2ModelAdapter-v0.5.5/pyproject.toml) | Python package/build metadata. |
| [`run_selftest.py`](adapter/C2ModelAdapter-v0.5.5/run_selftest.py) | Canonical adapter unit + router-combo + effective-route selftest entrypoint. |
| [`simulation/effective_route_v055.py`](adapter/C2ModelAdapter-v0.5.5/simulation/effective_route_v055.py) | Deterministic effective-route simulation. |
| [`simulation/router-combo-v055-results.json`](adapter/C2ModelAdapter-v0.5.5/simulation/router-combo-v055-results.json) | Shipped deterministic router-combo simulation result artifact. |
| [`simulation/router_combo_v055.py`](adapter/C2ModelAdapter-v0.5.5/simulation/router_combo_v055.py) | Deterministic opaque router-combo simulation. |
| [`tests/test_adapter.py`](adapter/C2ModelAdapter-v0.5.5/tests/test_adapter.py) | Adapter unit/regression tests. |
| [`tests/test_effective_route_v055.py`](adapter/C2ModelAdapter-v0.5.5/tests/test_effective_route_v055.py) | Effective-route v0.5.5 regression tests. |

The bundled package is self-contained as a distribution component. C2Cognitive consumes bounded adapter capability
evidence through its host-side contract; it does not make provider-native protocol state into durable C2 authority.

## Bundled adapter file surface

The bundled `adapter/C2ModelAdapter-v0.5.5/` tree contains 27 files: package metadata/documentation, the
`c2modeladapter` implementation modules, deterministic router/effective-route simulations, two test files, and the
`run_selftest.py` entrypoint. The public repository coverage matrix accounts for all 27 files individually.

The adapter's own `MODEL-COVERAGE.md` reports an admission registry rather than a promise that every listed endpoint
is live or reachable. Stable/preview/provisional/quarantine lifecycle labels remain part of capability admission.
Unknown future identities are not automatically promoted by model-name resemblance.

See [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md).
