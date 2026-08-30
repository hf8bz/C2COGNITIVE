# C2Cognitive Troubleshooting

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Provide a symptom-to-diagnosis map for common adoption, runtime, verification, adapter, memory, handoff, and
documentation problems without bypassing the canonical runbooks.

### Canonical implementation sources

- [C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md](C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md)
- [C2COGNITIVE-CLI-LAUNCHER-GUIDE.md](C2COGNITIVE-CLI-LAUNCHER-GUIDE.md)
- [blocker-handling.md](.agent/runbooks/blocker-handling.md)
- [browser-tooling-recovery.md](.agent/runbooks/browser-tooling-recovery.md)
- [context-compaction.md](.agent/runbooks/context-compaction.md)

---

## Quick diagnostic table

| Symptom | Check first | Safe response |
| --- | --- | --- |
| `C2PY_ERROR` | launcher/runtime availability | resolve launcher; do not silently install runtime |
| aggregate verifier appears stuck | identify current check/process; run the specific check if needed | do not call it PASS while running |
| release identity violation | `VERSION`, release metadata/current status | fix current release-facing references only; preserve historical evidence |
| broken Markdown link | `scripts/verify/links.py` output | correct target/path; do not suppress the check |
| no active Goal during product work | Goal gate/readiness | admit/resume a Goal before product writes |
| workflow-only tries to touch product source | entry mode scope | stop and switch/replan |
| BR-v2 cursor rejected | source generation/profile/digest changed | restart bounded read from fresh evidence |
| memory record not actionable | ACL/freshness/evidence/lifecycle | repair evidence or keep candidate/stale |
| Wiki invalid | source generations changed | rebuild/publish derived generation through canonical path |
| worker/loadout rejected | lease/session epoch/digest binding | reacquire/rebuild rather than reuse stale worker state |
| adapter import fails in bare pytest | adapter root/PYTHONPATH contract | use canonical `run_selftest.py` |
| model alias/profile rejected | adapter capability profile | fail closed or verify/add profile; do not trust name resemblance |
| cache miss | provider/runtime cache contract | continue correct non-cache path |
| CEA/BEA rejected | exact binding/TTL/session/incident | repropose; do not widen grant |

## Verification triage

Run the smallest relevant verifier first, then the aggregate suite when appropriate. A failing specific validator
gives more actionable evidence than repeatedly restarting `all.py`.

Useful examples:

```text
<C2PY> scripts/verify/release_identity.py
<C2PY> scripts/verify/links.py
<C2PY> scripts/verify/counts.py
<C2PY> scripts/verify/read_contract.py
<C2PY> scripts/verify/context_representation.py
<C2PY> scripts/verify/progress_liveness.py
```

## If context was compacted

Do not reconstruct state from confidence. Follow the handoff/resume contract, revalidate divergence, Goal/run
identity, and authority state, then resume the exact remaining work.

## If a tool is missing

Distinguish `declared`, `unverified`, `unavailable`, and truly required. GATE 0 does not execute candidate tools just
to prove availability. Missing optional tooling should narrow claims rather than force unsafe installation.

## If documentation and executable behavior disagree

Surface the contradiction. Do not silently edit history or choose whichever source is convenient. Current normative
control-plane/executable contracts outrank explanatory public docs.

## If you suspect a packaging defect

Fresh-extract the ZIP, compare paths/hashes against the staging manifest used for packaging, run ZIP CRC testing, then
run the relevant C2Cognitive verification from the extracted tree. Do not validate only the pre-ZIP staging tree and
assume extraction is identical.

---

## If a subsystem is not described in a topical guide

Do not infer behavior from a filename. Use the [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md)
to find the public owner, then inspect the actual shipped control-plane/script file. For runbook, schema/state,
prompt, script/verifier, or scope questions, use the corresponding exhaustive catalog. Public prose is explanatory;
actual executable/control-plane behavior remains the final implementation evidence.
