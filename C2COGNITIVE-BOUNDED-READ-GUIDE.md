# C2Cognitive Bounded Read (BR-v2) Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Document the bounded physical-ingestion contract that prevents a logically narrow retrieval request from becoming
an unbounded model-facing file read.

### Canonical implementation sources

- [CHANGELOG.md](CHANGELOG.md)
- [core.py](scripts/read/core.py)
- [jsonl.py](scripts/read/jsonl.py)
- [archive.py](scripts/read/archive.py)
- [workflow-discipline.md](.agent/runbooks/workflow-discipline.md)
- [context-compaction.md](.agent/runbooks/context-compaction.md)

---

## Why BR-v2 exists

Semantic retrieval budgets and filesystem ingestion budgets are different. A query can select one file and still
accidentally admit a huge minified line, oversized JSONL record, or archive into context. BR-v2 therefore constrains
the physical view itself.

## Cursor contract

The preferred Version 1 continuation path uses an opaque cursor bound to the source generation and prior view rather
than treating a human-readable line/character position as authority. The package documents the cursor as being bound
to repository-relative path, exact source-byte offset, local source generation, read profile, and prior-view digest.

Consequences:

- changing the source can stale the cursor;
- changing the read profile is not the same continuation;
- continuation does not silently raise the hard model-view ceiling;
- a cursor carried across compaction is evidence to revalidate, not independent resume authority.

## Bounded view rules

The current implementation enforces configured ceilings around the admitted model-facing view. Governed JSONL reads
should emit complete records rather than half-record fragments where the contract requires record integrity. Archive
handling remains bounded and does not turn a ZIP into implicit full extraction/read authority.

## Strategy review

Repeated blind sequential pagination is itself bounded. The Version 1 documentation specifies a strategy-review
outcome after repeated blind windows instead of silently converting bounded reading into endless scrolling.

At that point, choose a better retrieval strategy:

```text
targeted search
range selection
record-aware JSONL read
archive member selection
parser/structural tooling when authorized
or human/agent replanning
```

## Security and authority

A successful bounded read proves only that the physical read contract was satisfied. It does not make the content
trusted, fresh, relevant, normative, or authorized for action. Untrusted repository text is still data unless
separately admitted as instruction authority.

## Verification

Relevant current checks include the read-contract verifier and selftests in `scripts/selftest/`. Use the aggregate
suite only when you can wait for its bounded finite checks to complete; do not convert a still-running check into
PASS.

## Compatibility path

A human-readable line/character continuation may exist as a compatibility/manual path. It is not the preferred BR-v2
generation-bound authority.

---

## Repository coverage context

For exhaustive path-to-public-doc coverage across the shipped C2Cognitive v1.0.0 repository, see the
[Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md). This topical guide explains one subsystem;
it does not replace the full control-plane/script/schema catalogs.
