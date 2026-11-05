---
name: pck-workflow
description: Apply the contract throughout a file-changing task and complete three independent reviews within a bounded correction cycle.
---

# Work with the Project Contract

Use this workflow for changes to code, documentation, configuration, or the
contract. Discussion and read-only review assignments do not start another
review cycle.

## Work

Read the material selected by [the package entry](../../README.md). For an
installed project, read the PCK block in the project-root agent instruction file
and use only optional Skills listed there and present at their derived paths. If
the block is missing, malformed, duplicated, or lists an unknown or missing
Skill, hold the change until the installation is corrected. When maintaining PCK
itself, repository instructions and the package contents define the available
material; no installed-project declaration is required. If a task reaches an
unlisted required responsibility, hold the change until the installation and
its dependencies are updated under the project's existing authorization.
Establish the authorized scope, affected responsibilities, owners, data flow,
lifetimes, interfaces, and failure boundaries. Follow project branch policy;
track the task's cumulative changes from its baseline, including commits,
uncommitted work, additions, moves, and deletions. Exclude unrelated changes.

Implement and self-review complete responsibility units with their controlling
clauses and exceptions at hand. Check local EIB boundaries separately from
ownership and failure behavior, and apply language rules to actual declarations
and expressions. Use original numbered lines when layout matters. The main
agent performs required builds, tests, and runtime validation.

## Recover context

After compaction or summary-based resumption, every agent rereads applicable
agent instructions and, for an installed project, the PCK block in the
project-root agent instruction file. Then reread the package entry, this
workflow, all core Skills, the project entry and required shared topics, and
complete applicable topics, language and platform Skills, their references, and
examples. Contract work also rereads pck-maintain and its writing guide. Retrieve
truncated portions; summaries locate progress, not requirements.

Reconcile current files and user decisions with the task baseline, scope,
permissions, exclusions, models, active work, findings, validation, and review
round count. Preserve outstanding obligations and briefly report the actual
rereading and gaps before continuing. Hold work that depends on missing material.

## Independent review

When modifications are ready, freeze the file state and obtain three separate,
independent reviews, concurrently where supported:

| Assignment | Responsibility |
| --- | --- |
| `pck_review_structure` | Consistency First and EIB: local operation boundaries, responsibilities, interfaces, data flow, ownership, lifetime, and failure behavior. |
| `pck_review_style` | Direct Statements and every applicable language rule and project style choice, applied to actual source forms. |
| `pck_review_project` | Applicable platform and project obligations, conditions, exceptions, authorization, and validation evidence. |

Honor explicit model assignments; role-specific assignments override the shared
`pck_review` assignment at the same authority level. Otherwise select a capable,
economical, fast model from available options. If launch fails, retry with the
main agent's model and disclose it; another failure leaves the review incomplete.

Give reviewers the scope, authorized decisions, baseline, cumulative changes,
repository and contract locations, and role. Do not pass the main agent's
reasoning or any reviewer's conclusions. Reviewers read required material before
judging source, and may inspect history, callers, owners, and suitable precedents.
They work read-only: no edits, builds, tests, validators, application runs,
commits, or further agents. Each may retain its independent context for later
rounds, reconciling current content and recovering after compaction.

Review complete units against the applicable original clauses, including their
exceptions. Report the source observations supporting the judgment: actual
operation handoffs for EIB, actual declarations and expressions for style.
Cite precise original lines and requirements; do not reconstruct source.
Keep findings within defects introduced or materially affected by the cumulative
change. Contract review compares maintained requirements with the pre-edit
contract and authorized decisions. State coverage and evidence gaps; reading,
fact extraction, or a preferred alternative alone does not establish conformance
or a violation. Assigned roles do not waive compatible requirements.

## Resolve and finish

A round includes all three reviews of the same file state and the main agent's
assessment. Allow at most three rounds; corrections do not reset the count.
Collect all results before editing. Assess findings against original source and
requirements. Request a focused evidence recheck for contradictions or omissions
without prescribing the verdict. Missing evidence or review coverage is incomplete.

The main agent may accept or veto findings. For each veto, disclose the reviewer,
requirement, location, proposal, reason, and affected scope or uncertainty.
A veto cannot waive required review, change requirements, or turn missing or failed
validation into a pass. Identify acceptance that relies on vetoes.

After corrections, repeat affected validation and all three reviews of the
cumulative change. Any further content change requires review within the same
limit. After round three, stop automatic correction and hand unresolved findings,
disputes, or incomplete reviews to the user; do not commit, push, or claim acceptance.

Complete only when all three reviews cover the final content, findings are
resolved or openly vetoed, and applicable project validation is complete.
Report scope, rounds, actual models and fallbacks, vetoes, validation, and limits.
Keep task and review evidence in the conversation, without PCK state files,
checklists, input archives, or review histories. Publishing requires authorization.
