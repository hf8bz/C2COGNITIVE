# C2Cognitive Emergency Authority Guide

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain the two emergency authority planes shipped by C2Cognitive - Cognitive Emergency Authorization (CEA) and
Bounded Emergency Authority (BEA) - and the rule that they remain independent, exact, expiring overlays rather than
wildcard permission.

### Canonical implementation sources

- [emergency-authority.schema.md](.agent/emergency-authority.schema.md)
- [bounded-emergency-authority.schema.md](.agent/bounded-emergency-authority.schema.md)
- [emergency-authority.md](.agent/runbooks/emergency-authority.md)
- [bounded-emergency-authority.md](.agent/runbooks/bounded-emergency-authority.md)
- [emergency](scripts/emergency/)

---

## Two separate planes

| Plane | Purpose | What it may authorize | What it never inherits |
| --- | --- | --- | --- |
| CEA | contain/purge affected persistent cognition | exact cognitive effects in the CEA contract | repository/product write authority |
| BEA | emergency repository repair | exact forward repository writes already materialized in scope | CEA cognitive authority |

The separation is deliberate. A cognition incident can require CEA without a repository write. A source repair can
require BEA without giving permission to purge memory. When both are needed, obtain both exact grants.

## Shared safety properties

Emergency authority should remain:

- human-granted at the host boundary;
- exact in incident/run/session/Goal binding where required;
- exact in target/action;
- time-bounded/expiring;
- auditable;
- non-wildcard;
- revocable or automatically expired;
- and incapable of bypassing unrelated semantic scope.

## CEA

See [C2COGNITIVE-CEA-GUIDE.md](C2COGNITIVE-CEA-GUIDE.md). CEA-CONTAIN is monotone-restrictive; CEA-PURGE is the
stronger exceptional path for the governed security purge mechanism.

## BEA

BEA is an emergency overlay on an exact repository-write plan. It does not authorize a vague directory, an unknown
future mutation, or a rollback bypass. ACRP/cache/model routing are non-authoritative to the BEA scope.

## Host approval identity

The repository validates the grant contract it receives. The host is responsible for authenticating the human approver
and protecting approval/check endpoints from untrusted workers/content. Do not describe a local grant as a
cryptographic signature unless an external signing system actually provides that property.

## Incident rule

Emergency does not mean "skip verification." The intended order is containment/authorization, exact effect,
verification, and expiration/revocation. If the effect discovers new targets, return to proposal/planning instead of
silently widening the grant.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
