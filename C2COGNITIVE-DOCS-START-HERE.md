# C2Cognitive Documentation  -  Start Here

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**
**Author:** Hafizh Al-Banna

> **Documentation status:** public explanatory guide. This file does not override `AGENTS.md`, `.agent/config.yml`, current scopes/runbooks/schemas, entry prompts, or executable validators. Where prose conflicts with an executable contract, surface the contradiction and follow the canonical contract.

[Docs start](C2COGNITIVE-DOCS-START-HERE.md)  |  [Deep dive](C2COGNITIVE-DEEP-DIVE.md)  |
[Reference](C2COGNITIVE-REFERENCE.md)  |  [File map](C2COGNITIVE-FILE-MAP.md)  |
[Troubleshooting](C2COGNITIVE-TROUBLESHOOTING.md)

## Purpose

Provide the public navigation surface for the complete root documentation set and explain how public explanatory
docs relate to the canonical executable contracts shipped with C2Cognitive.

### Canonical implementation sources

- [README.md](README.md)
- [START-HERE.md](START-HERE.md)

---

## Which document do I need?

| I need to... | Read |
| --- | --- |
| Understand the whole architecture | [`C2COGNITIVE-DEEP-DIVE.md`](C2COGNITIVE-DEEP-DIVE.md) |
| Choose adoption mode | [`C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md`](C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md) |
| Install governance only | [`C2COGNITIVE-WORKFLOW-ONLY-GUIDE.md`](C2COGNITIVE-WORKFLOW-ONLY-GUIDE.md) |
| Give an agent workflow-only instructions | [`C2COGNITIVE-WORKFLOW-ONLY-AGENT-INSTRUCTION.md`](C2COGNITIVE-WORKFLOW-ONLY-AGENT-INSTRUCTION.md) |
| Understand exact writes/rollback | [`C2COGNITIVE-ACTUAL-WRITE-PLAN-ROLLBACK-GUIDE.md`](C2COGNITIVE-ACTUAL-WRITE-PLAN-ROLLBACK-GUIDE.md) |
| Understand safe initial discovery | [`C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md`](C2COGNITIVE-SAFE-GATE0-ROLLBACK-GUIDE.md) |
| Read large evidence safely | [`C2COGNITIVE-BOUNDED-READ-GUIDE.md`](C2COGNITIVE-BOUNDED-READ-GUIDE.md) |
| Handle blockers | [`C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md`](C2COGNITIVE-BLOCKER-CONVERGENCE-GUIDE.md) |
| Handle resource/session resume | [`C2COGNITIVE-BUDGET-RESUME-GUIDE.md`](C2COGNITIVE-BUDGET-RESUME-GUIDE.md) |
| Resolve Python launcher notation | [`C2COGNITIVE-CLI-LAUNCHER-GUIDE.md`](C2COGNITIVE-CLI-LAUNCHER-GUIDE.md) |
| Understand adapter/cache boundary | [`C2COGNITIVE-MODEL-ADAPTER-GUIDE.md`](C2COGNITIVE-MODEL-ADAPTER-GUIDE.md) |
| Understand ACRP | [`C2COGNITIVE-ACRP-GUIDE.md`](C2COGNITIVE-ACRP-GUIDE.md) |
| Read ACRP in Indonesian | [`C2COGNITIVE-ACRP-GUIDE-ID.md`](C2COGNITIVE-ACRP-GUIDE-ID.md) |
| Understand CEA | [`C2COGNITIVE-CEA-GUIDE.md`](C2COGNITIVE-CEA-GUIDE.md) |
| Read CEA in Indonesian | [`C2COGNITIVE-CEA-GUIDE-ID.md`](C2COGNITIVE-CEA-GUIDE-ID.md) |
| Understand CEA/BEA taxonomy | [`C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE.md`](C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE.md) |
| Read emergency authority in Indonesian | [`C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE-ID.md`](C2COGNITIVE-EMERGENCY-AUTHORITY-GUIDE-ID.md) |
| Review liveness/self-audit in English | [`C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md`](C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-EN.md) |
| Review liveness/self-audit in Indonesian | [`C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-ID.md`](C2COGNITIVE-PROGRESS-LIVENESS-SELF-AUDIT-ID.md) |
| Handle untrusted/sensitive content | [`C2COGNITIVE-SECRET-SAFETY-PHASE3-GUIDE.md`](C2COGNITIVE-SECRET-SAFETY-PHASE3-GUIDE.md) |
| Diagnose failures | [`C2COGNITIVE-TROUBLESHOOTING.md`](C2COGNITIVE-TROUBLESHOOTING.md) |
| Find a file | [`C2COGNITIVE-FILE-MAP.md`](C2COGNITIVE-FILE-MAP.md) |
| Look up stable concepts/paths | [`C2COGNITIVE-REFERENCE.md`](C2COGNITIVE-REFERENCE.md) |
| See public documentation entry | [`C2COGNITIVE-DOCS-START-HERE.md`](C2COGNITIVE-DOCS-START-HERE.md) |

## Public documentation model

The public documentation surface lives at repository root. Use these guides for explanation and navigation, then
follow the matching `AGENTS.md`, `.agent` runbook/schema/scope, entry prompt, or executable validator when performing
an operation. Public prose does not become a second source of execution authority.

## Reading order for a new operator

1. `README.md`
2. this file
3. `C2COGNITIVE-ENTRY-MODE-DECISION-MATRIX.md`
4. the guide matching your immediate operation
5. `C2COGNITIVE-REFERENCE.md` for lookup
6. canonical runbook/schema/script when executing a procedure

## Authority rule

Public docs explain. `AGENTS.md`, current `.agent/config.yml`, current runbooks/scopes/schemas, entry prompts, and
executable validators govern. Do not promote this navigation layer into a second control plane.

---

## Exhaustive repository references

For full-repository coverage rather than topic-only navigation, use:

| Need | Public document |
| --- | --- |
| Prove every non-internal shipped path has a documentation owner | [Repository Coverage Matrix](C2COGNITIVE-REPOSITORY-COVERAGE-MATRIX.md) |
| Inspect all 40 Core rules, scopes, and routing metadata | [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md) |
| Inspect all 313 config keys and 235 thresholds | [Configuration Reference](C2COGNITIVE-CONFIGURATION-REFERENCE.md) |
| Inspect every shipped runbook | [Runbook Catalog](C2COGNITIVE-RUNBOOK-CATALOG.md) |
| Inspect schemas and runtime-state surfaces | [Schema and Runtime State Catalog](C2COGNITIVE-SCHEMA-STATE-CATALOG.md) |
| Inspect all entry/staged/resume prompts | [Prompt Catalog](C2COGNITIVE-PROMPT-CATALOG.md) |
| Inspect all 103 scripts and 63 registered check invocations | [Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md) |
| Understand memory/Skills/structural/Wiki/failure/lesson lifecycle | [Cognitive State Lifecycle Guide](C2COGNITIVE-COGNITIVE-STATE-LIFECYCLE-GUIDE.md) |
| Understand discovery, indexing, dispatch, loadouts, leases and batching | [Agent, Discovery and Orchestration Guide](C2COGNITIVE-AGENT-DISCOVERY-ORCHESTRATION-GUIDE.md) |
| Understand domain scopes and mobile/payment/QA lanes | [Application Lanes Guide](C2COGNITIVE-APPLICATION-LANES-GUIDE.md) |
| Install/adopt/bootstrap safely | [Install, Adopt and Bootstrap Guide](C2COGNITIVE-INSTALL-ADOPT-BOOTSTRAP-GUIDE.md) |
| Understand evidence/provenance/attestations/compliance/verification | [Evidence, Provenance and Assurance Guide](C2COGNITIVE-EVIDENCE-PROVENANCE-ASSURANCE-GUIDE.md) |

The public-doc set is intentionally broader than a curated quick-start list because C2Cognitive v1.0.0 ships a large
control-plane surface. The coverage matrix is the audit anchor when deciding whether a repo file/family is publicly
represented.
## v1.0.2 terminal hardening

Start with `C2COGNITIVE-TERMINAL-RECONCILIATION-GUIDE.md` when a completed run appears resumable, when a stale cursor remains open, or when repeated successor runs are being created only to reconcile prior state.
