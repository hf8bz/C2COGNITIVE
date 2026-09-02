# C2Cognitive Prompt Catalog

**C2Cognitive v1.0.2  |  Corrective Release 3  |  Public release  |  2 September 2026**

## Purpose

C2Cognitive v1.0.0 ships three repository-entry prompts and thirteen staged/continuity prompts. This catalog makes
the complete prompt surface visible without requiring visitors to infer it from filenames.

## Entry prompts

The three root entry prompts select repository state and intended outcome:

* `SCAN-AND-ADOPT.prompt.md` - existing repository, adoption that can proceed into an implementation Goal;
* `INSTALL-WORKFLOW-ONLY.prompt.md` - existing repository, install/repair only, no product-behavior mutation;
* `BOOTSTRAP-NEW-REPO.prompt.md` - empty/new repository driven from planning artifacts rather than existing code.

## Complete prompt inventory

| Prompt | Shipped title | Role / activation summary |
| --- | --- | --- |
| [`SCAN-AND-ADOPT.prompt.md`](SCAN-AND-ADOPT.prompt.md) | SCAN & ADOPT - one prompt for a repo that already exists | For a repo that **already has code**. When the repo is still empty, use `BOOTSTRAP-NEW-REPO.prompt.md`. |
| [`INSTALL-WORKFLOW-ONLY.prompt.md`](INSTALL-WORKFLOW-ONLY.prompt.md) | INSTALL WORKFLOW ONLY - existing repo, no goal required | Use this entry point only when the repository already contains project content and the requested change is to install, repair, upgrade, or verify the C2Cognitive workflow/control plane itself. This entry point exists so a repository with no goal, an empty goal ledger, or only terminal goals can receive the workflow before the human creates the next implementation goal. |
| [`BOOTSTRAP-NEW-REPO.prompt.md`](BOOTSTRAP-NEW-REPO.prompt.md) | BOOTSTRAP - one prompt for a new or still-empty repo | For a folder that **does not contain code yet**. When code already exists, use `SCAN-AND-ADOPT.prompt.md`. |
| [`prompts/00-baseline-audit.prompt.md`](prompts/00-baseline-audit.prompt.md) | PROMPT 00 - Baseline Audit (READ-ONLY) | Read-only with respect to the repo. The only write that is permitted: `docs/graph-engineering/00-audit.md`. Changing code, config, or rules is forbidden. |
| [`prompts/01-measurable-loop.prompt.md`](prompts/01-measurable-loop.prompt.md) | PROMPT 01 - Measurable Loop | Prerequisite: PROMPT 00 is complete. **Do not skip this prompt.** Every later prompt produces claims that cannot be proven without this step. |
| [`prompts/02-lessons-corpus.prompt.md`](prompts/02-lessons-corpus.prompt.md) | PROMPT 02 - Lesson Corpus | Prerequisite: PROMPT 00. Its value is proportional to the size of the lesson notes that already exist - below 100 lines, defer it. |
| [`prompts/03-graph-plane.prompt.md`](prompts/03-graph-plane.prompt.md) | PROMPT 03 - The Graph Plane | Prerequisite: PROMPT 01 has been running for at least 6 weeks. Running this too early produces a tidy graph that is empty of meaning. |
| [`prompts/04-context-split.prompt.md`](prompts/04-context-split.prompt.md) | PROMPT 04 - Context Split | Prerequisites: PROMPT 00, and PROMPT 01 already has a baseline. This is the riskiest prompt in the whole sequence, because it changes the rulebook that is currently in use. |
| [`prompts/05-retrieval-eval.prompt.md`](prompts/05-retrieval-eval.prompt.md) | PROMPT 05 - Retrieval Evaluation | Prerequisites: PROMPT 04, and the corpus partitions are already defined. |
| [`prompts/06-operations.prompt.md`](prompts/06-operations.prompt.md) | PROMPT 06 - Operations | Prerequisites: PROMPT 01 and PROMPT 04. |
| [`prompts/07-compaction-drill.prompt.md`](prompts/07-compaction-drill.prompt.md) | Prompt 07 - Compaction Drill | A rehearsal. You run this deliberately, on a real task, to find out whether the handoff mechanism actually works in **your** CLI or IDE before you depend on it during real work. |
| [`prompts/08-goal-emit.prompt.md`](prompts/08-goal-emit.prompt.md) | Prompt 08 - Emit the Goal | Paste this when the requirements are complete and you want an implementation that runs without stopping to ask what comes next. |
| [`prompts/09-memory-semantic-extraction.prompt.md`](prompts/09-memory-semantic-extraction.prompt.md) | Prompt 09 - Semantic memory extraction proposal | Use this prompt only after a significant event, verified fact, recurring scenario, or stable project/team/persona observation has evidence worth preserving. Do not copy raw conversation logs into memory. |
| [`prompts/97-budget-resume.prompt.md`](prompts/97-budget-resume.prompt.md) | PROMPT 97 - Resume After Budget / Resource Suspension | Use this prompt in a new CLI/session when the previous C2Cognitive run ended with `RUN_OUTCOME: suspended_resumable`, especially after `budget_soft_boundary`, `budget_hard_exhausted`, `context_pressure`, `rate_limit`, or `host_session_end`. |
| [`prompts/98-compaction-handoff.prompt.md`](prompts/98-compaction-handoff.prompt.md) | Prompt 98 - Compaction Handoff | > Resource-budget note: Prompt 98 is for compaction/durable continuity. If the trigger is a budget, rate-limit, host-session, or CLI resource boundary, emit the portable capsule from `.agent/resume-capsule.schema.md` and resume with Prompt 97. A target `.agent/state/**` write is never required merely to make a resource suspension resumable. |
| [`prompts/99-session-resume.prompt.md`](prompts/99-session-resume.prompt.md) | PROMPT 99 - Resuming a Long Session | > Resource-budget routing: when the prior run ended `RUN_OUTCOME: suspended_resumable`, use Prompt 97 first. Prompt 99 remains the durable session-resume path; it MUST NOT force a PHASE restart or require `.agent/state/**` when a valid portable capsule survives. |

## Sequence semantics

The numbered prompts are not interchangeable. `00` establishes baseline audit evidence; `01` creates a measurable
loop; later graph/context/retrieval/operations stages build on those preconditions. `07` rehearses compaction,
`08` emits a persistent Goal only after readiness, and `09` proposes semantic memory extraction rather than copying
raw conversation logs. `97`, `98`, and `99` are distinct continuity paths for resource suspension, compaction
handoff/rehydration, and durable long-session resume.

See [Install, Adopt and Bootstrap Guide](C2COGNITIVE-INSTALL-ADOPT-BOOTSTRAP-GUIDE.md) and
[Budget & Resume Guide](C2COGNITIVE-BUDGET-RESUME-GUIDE.md).
