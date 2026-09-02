# C2Cognitive Evidence, Provenance and Assurance Guide

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

This guide consolidates evidence contracts, requirement provenance, execution provenance, attestations, compliance
mapping, retrieval evaluation, validators, and selftests so public documentation can explain what a C2Cognitive
"PASS" does and does not mean.

## Evidence before claims

CORE-04 requires evidence before patching and CORE-05 forbids claims without artifacts. Evidence can be file/line
material, tool output, a bounded read receipt, validator output, or other explicit artifacts admitted by the active
workflow. A summary or remembered statement is not automatically current evidence.

## Requirements provenance

`.agent/requirements.schema.md` preserves requirement identity and provenance rather than letting an inference become
a repository requirement by repetition. Goal readiness is downstream of requirements/acceptance/ambiguity state;
Goal persistence does not repair an incomplete requirement set.

## Execution provenance

`.agent/provenance.schema.md` and `scripts/provenance/export.py` support provenance records and W3C PROV-O JSON-LD
export. Digest chaining is integrity evidence; it is not cryptographic authorship/identity proof by itself.

## Release-claim attestations

`.agent/attestations.schema.md` and `.agent/attestations.jsonl` can bind a claim to the subject/evidence artifacts used
to derive it. The schema explicitly does not turn the record into a digital signature or proof of scientific
generalizability.

## Compliance evidence mapping

`.agent/compliance-map.md` maps shipped evidence/rules to selected control structures such as SOC 2, PCI DSS, and
EU AI Act concepts. This is evidence mapping only. It is not certification and cannot replace organizational policy,
training, legal review, assessor judgment, or external controls.

## Retrieval evaluation

`eval/retrieval/golden.example.jsonl` provides the example golden-set shape. `eval/rubrics/_TEMPLATE.md` is a rubric
template. The golden verifier checks identifiers, kinds, partitions, and must-not-match structure; it does not prove
that a target repository has high retrieval quality until a real target golden set and measurements exist.

## Verification stack

The repository carries:

* deterministic corpus/contract validators;
* Goal/handoff/graph/JSONL gates;
* populated selftests;
* adversarial/fault/concurrency/security/regression harnesses;
* adapter unit/simulation testing in the bundled adapter package.

`verify/all.py` registers 63 invocations. For the v1.0.2 freeze they were executed process-isolated after the aggregate wrapper timed out; all 63 passed per edition. Some checks can be vacuous in a pristine template; vacuity is reported
rather than relabeled as populated behavior.

## Tests versus prose

CORE-29 states that executable behavior is extracted from tests first and documents second. A contradiction between
executable behavior and prose is surfaced as a contradiction; it is not silently resolved in favor of whichever
source is convenient.

## Claim limits

The following distinctions remain explicit:

```text
validator PASS        != universal correctness
selftest PASS         != production-environment proof
synthetic simulation  != live provider traffic
compliance map        != certification
provenance digest     != author identity
cache observation     != evidence authority
activity              != semantic progress
```

See [Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md) and
[Reference](C2COGNITIVE-REFERENCE.md).
