# C2Cognitive Adaptive Context Representation Planning (ACRP)

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain how C2Cognitive may optimize the model-facing representation of an already admitted semantic set without
changing evidence membership, trust, freshness, write authority, or completion semantics.

### Canonical implementation sources

- [84-context-representation-planner.md](.agent/runbooks/context-representation.md)
- [context-representation.schema.md](.agent/context-representation.schema.md)
- [context-representation.md](.agent/runbooks/context-representation.md)
- [model-adapter.md](.agent/runbooks/model-adapter.md)

---

## Position in the cognition pipeline

ACRP is downstream of canonical selection. The safe ordering is:

```text
repository / governed memory / verified Skill / structural candidate
                    |
                    v
        trust + ACL + freshness + evidence checks
                    |
                    v
          freeze ordered semantic selection
                    |
                    v
                   ACRP
                    |
                    v
       effective-route model-adapter boundary
                    |
                    v
                    LLM
```

The representation layer is not allowed to decide that an additional record is relevant after the selection has been
frozen. Representation optimization and semantic admission are different decisions.

## Runtime modes

The current Version 1 contract recognizes a conservative native path and bounded transformed representations described
by the current profile/plan schema. Any transformed representation must remain reversible enough for the contract
being exercised, route-bound where required, and incapable of manufacturing evidence.

A productivity signal may justify a representation choice. It cannot justify:

- adding a memory record that failed ACL or freshness;
- promoting an unverified Skill;
- widening a Goal;
- widening an `ACTUAL_WRITE_SET`;
- converting cache telemetry into correctness evidence;
- or reporting completion.

## Failover rule

Model failover is an effective-route change. A representation profile that was admitted for one stable runtime/model
family is not automatically valid for another family. When the binding cannot be proven for the new effective route,
the safe behavior is to fall back to the admitted native/default representation path.

Physical aliases may be handled by the adapter only when their canonical capability identity remains within the
verified profile. Provider cache identity remains isolated even when semantic representation compatibility is
preserved.

## Authority non-interference

ACRP is intentionally non-authoritative:

```text
ACRP mode             != evidence membership
ACRP productivity     != correctness
ACRP compression      != permission to write
ACRP route telemetry  != durable cognitive truth
```

Security policy, exact authority objects, rollback evidence, emergency grants, and other authority-bearing artifacts
should not be silently transformed in a way that changes their canonical meaning.

## Verification

Use the shipped launcher rather than assuming a literal `python3` command:

```text
<C2PY> scripts/verify/context_representation.py
<C2PY> scripts/selftest/context_representation.py
<C2PY> scripts/selftest/fullstack_interactions.py
```

`<C2PY>` is documentation notation. Resolve it through
[C2COGNITIVE-CLI-LAUNCHER-GUIDE.md](C2COGNITIVE-CLI-LAUNCHER-GUIDE.md).

## Claim boundary

A passing ACRP selftest supports the tested representation contract. It does not prove that a provider will produce a
cache hit, that compressed context improves reasoning on every task, or that all model families preserve equivalent
semantics.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
