---
name: pck-workflow
description: Apply the contract, self-review changes, and select independent reviews and rounds according to task needs.
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

The main agent selects review roles from the change's scope, risk, and open
questions, subject to user and project requirements. It may skip all review
agents when self-review suffices; state the reason. Self-review still covers all
applicable Skills and project obligations. When independent review is needed,
use one round by default; the user may specify another round count or roles.

| Assignment | Review need |
| --- | --- |
| `pck_review_structure` | Consistency First and EIB when changes affect design boundaries: responsibilities, interfaces, data flow, ownership, lifetime, or failure behavior. |
| `pck_review_style` | Independent scrutiny of Direct Statements, language forms, or project style. |
| `pck_review_project` | Independent scrutiny of platform or project obligations, authorization, or validation evidence. |

Freeze the file state and obtain only the selected reviews, independently and
concurrently where supported. Honor explicit model assignments; role-specific
assignments override the shared `pck_review` assignment at the same authority
level. Otherwise select a capable, economical, fast model. If launch fails, retry
with the main agent's model and disclose it; another failure leaves review incomplete.

Give reviewers the scope, authorized decisions, baseline, cumulative changes,
repository and contract locations, and role, without the main agent's reasoning
or other verdicts. Reviewers read required originals and may inspect history,
callers, owners, and precedents. They work read-only: no edits, builds, tests,
validators, application runs, commits, or further agents. Later rounds may reuse
their independent context, recovering after compaction.

Review complete units against original clauses and exceptions. Cite precise
original lines and actual operation handoffs, declarations, and expressions.
Limit findings to defects introduced or materially affected by the cumulative
change; contract review compares the pre-edit contract and authorized decisions.
State coverage and evidence gaps. Reading, fact extraction, or a preferred
alternative alone establishes neither conformance nor a violation. Assigned
roles do not waive compatible requirements.

## Resolve and finish

A round includes all selected reviews of the same file state and the main
agent's assessment. Collect all results before editing. Assess findings against
originals; request focused evidence rechecks without prescribing the verdict.
Missing evidence or required review coverage is incomplete.

Accept or veto findings against the requirements. Disclose each veto's reviewer,
requirement, location, proposal, reason, and remaining uncertainty. A veto cannot
waive required review or validation. After corrections, self-review the final
content and repeat affected validation. Further independent rounds stay within
the user's round count; corrections do not reset it. At the limit, stop automatic
review and report unresolved findings or incomplete required reviews; do not
publish or claim acceptance while they remain.

Complete when final self-review, selected reviews and applicable validation are
complete, with findings resolved or openly vetoed. Report review choices or skips,
rounds, actual models and fallbacks, vetoes, validation, and limits in the
conversation. Do not create PCK state files or review histories. Publishing
requires authorization.
