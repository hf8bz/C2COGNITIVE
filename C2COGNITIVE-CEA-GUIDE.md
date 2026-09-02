# C2Cognitive Cognitive Emergency Authorization (CEA)

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain the emergency authority used to contain or purge affected persistent-cognition objects without inheriting
repository/product write authority.

### Canonical implementation sources

- [emergency-authority.schema.md](.agent/emergency-authority.schema.md)
- [emergency-authority.md](.agent/runbooks/emergency-authority.md)
- [cognitive_authority.py](scripts/emergency/cognitive_authority.py)
- [cognitive_effect.py](scripts/emergency/cognitive_effect.py)
- [memory-lifecycle.md](.agent/runbooks/memory-lifecycle.md)

---

## What CEA governs

CEA exists for exceptional repair of persistent cognition. Version 1 distinguishes two classes:

- **CEA-CONTAIN**  -  monotone-restrictive actions such as retiring affected memory/Skill state, revoking an affected
  worker/session path, or invalidating derived Wiki actionability where the exact contract allows it.
- **CEA-PURGE**  -  stronger explicit approval for the existing `SECURITY_PURGE` exceptional repair path.

CEA is not repository write authority.

## Canonical incident flow

```text
DETECT
  v
DEFENSIVE SUPPRESSION
  v
BOUND EXACT AFFECTED OBJECT SET
  v
CEA PROPOSAL
  v
HUMAN APPROVAL AT HOST BOUNDARY
  v
CANONICAL C2COGNITIVE EFFECT
  v
TRANSITIVE INVALIDATION / REVOCATION AS DECLARED
  v
VERIFY
  v
AUTO-REVOKE / EXPIRE GRANT
```

Detection can defensively suppress actionability; detection cannot grant itself stronger repair authority.

## Exact binding

A proposal/grant is bound to exact incident/run/session/Goal context as required by the schema, exact typed objects,
exact actions, and TTL/expiry. CEA does not claim to compute an unrestricted general dependency closure. The proposal
must enumerate the affected set the implementation can actually justify.

## CEA and BEA do not inherit each other

If an incident requires both cognitive containment and repository repair, obtain the matching CEA authority for
cognitive effects and the matching normal/BEA authority for repository writes. One grant never becomes the other.

## Human approval boundary

The repository package can validate proposal/grant structure and effect binding. Authentication of the human approver
is a host responsibility. A local JSON grant is not, by itself, cryptographic proof of publisher identity.

## Verification

Use the shipped CEA proposal/check/effect commands and the emergency/cognitive invariant verification paths. The exact
CLI arguments are owned by the current scripts and schema; do not copy a stale command from prose when `--help`/source
indicates the interface changed.

## Claim boundary

CEA reduces the risk that compromised/stale cognitive objects remain actionable. It does not prove complete
eradication from every external cache, provider state, backup, conversation transcript, or system outside the governed
C2Cognitive stores.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
