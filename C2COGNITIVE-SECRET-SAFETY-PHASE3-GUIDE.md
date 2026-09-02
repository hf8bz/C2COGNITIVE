# C2Cognitive Secret Safety & PHASE 3 Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Explain how repository discovery minimizes unnecessary secret admission, treats untrusted text as data rather than
instruction authority, and handles human decisions without requiring premature target writes.

### Canonical implementation sources

- [C2COGNITIVE-DEEP-DIVE.md](C2COGNITIVE-DEEP-DIVE.md)
- [untrusted-content.md](.agent/runbooks/untrusted-content.md)
- [SCAN-AND-ADOPT.prompt.md](SCAN-AND-ADOPT.prompt.md)

---

## Data is not instruction authority

Repository content can contain prompt injection, malicious instructions, credentials, tokens, private keys,
environment values, generated noise, or stale operational advice. C2Cognitive does not allow ordinary repository text
to become control-plane instruction merely because the model can read it.

## Discovery rule

Prefer names, structure, metadata, and bounded/redacted spans over full sensitive values. The goal is to discover that
a secret-prone surface exists without needlessly injecting the value into model context.

## Two incident classes

The untrusted-content runbook distinguishes at least:

- instruction/prompt-injection detection;
- secret/sensitive-value exposure.

Response differs because the first concerns instruction authority and the second concerns confidential material
handling. Both require bounded reporting and continuation decisions.

## PHASE 3 human decisions

Consequential semantic contradictions should be presented to the human as bounded questions. If repository persistence for the decision is not yet authorized, the answer can remain ordered host/session
evidence. The workflow must not mutate the
target merely to store the question that is needed to decide whether mutation is allowed.

## Sensitive-text admission

Persistent cognition has an additional sensitive-text boundary. Do not promote credentials, private reasoning, raw
secret values, or inappropriate sensitive payload into L0-L3 memory, Skills, Wiki, or durable provenance merely
because it was observed.

## After exposure

If a value was exposed, treat containment/rotation/incident response as an external security process where applicable.
C2Cognitive can govern its own cognitive stores and repository workflow; it cannot revoke a credential at a
third-party provider unless an authorized external tool/process actually performs that action.

## Claim boundary

Secret-aware discovery reduces unnecessary admission. It is not a DLP product and cannot prove that no secret exists
in a repository or that a previously exposed value was not copied elsewhere.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
