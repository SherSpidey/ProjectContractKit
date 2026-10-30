---
name: pck-workflow
description: Carry a file-changing task from contract reading through three independent reviews, evidence-based corrections, and a bounded completion decision.
---

# Work with the Project Contract

Follow this workflow from the start of a task that changes code, documentation,
configuration, or the contract. Before declaring the current round of changes
complete, the main agent must obtain the three independent reviews below.
Discussion without file changes does not trigger these reviews. A review-only
assignment ends with its findings and does not start another review workflow.

## Start the task

Read [the package entry](../../README.md), all three core Skills, the project
entry and applicable topics, and the relevant language profiles and their rule
references. For contract work, also use
[pck-maintain](../pck-maintain/SKILL.md). Apply the package's authority rules to
the task, the reviewers, and model assignments.

Identify the authorized scope and the responsibilities, owners, data flow,
lifetimes, affected interfaces, and failure boundaries. Follow the project's
branch policy and existing local change tracking to identify this task's
baseline and cumulative changes, including commits, staged and unstaged edits,
new files, moves, and deletions. Keep unrelated changes outside that scope.
Use the existing task record; no separate PCK state file or change ledger is
required.

Treat the three independent reviews as a completion requirement from the start.
Implement within the agreed decisions and run the project's applicable
validation as the main agent. Reviewers examine code and evidence; the main
agent remains responsible for required builds, tests, and runtime checks.

## Select the review models

Use these stable assignment names:

| Assignment | Scope |
| --- | --- |
| `pck_review` | Shared model assignment for all three reviewers. |
| `pck_review_structure` | Consistency First and Everything Is a Block. |
| `pck_review_style` | Direct Statements and applicable language profiles. |
| `pck_review_project` | The applicable project contract. |

These names identify review assignments. Supply them through the host's
supported naming or role mechanism. A name alone does not register an agent or
configure its model.

Resolve explicit model assignments from the host's configuration and applicable
instructions first. Within the same instruction priority, a role-specific
assignment overrides `pck_review`. Use the assigned model directly and skip
autonomous selection for that role. For example, an instruction can say:

```text
Use model A for pck_review and model B for pck_review_project.
```

For an unassigned role, choose a sufficiently capable, economical, fast model
from the host's actual available options. Match capability to the review's
reasoning demands. Do not hardcode model names, assume access from a public
model catalog, or enumerate unsupported models by trial and error.

If selection fails or the selected model cannot start, retry that role with the
main agent's current model and disclose the fallback. Set that model explicitly
when supported, or use the host's documented parent-model inheritance. If the
fallback also cannot start, report that review as incomplete. A finding is a
normal review result and does not trigger model fallback.

## Review the completed changes

The main agent starts review when it considers this round's modifications
finished, before declaring completion. A commit is not needed to trigger review.
Pause modifications while the reviewers examine the same current file state.
Use the host's independent subagent capability for three separate contexts;
where supported, run them concurrently.

Give each reviewer the task and authorized decisions, repository locations,
the task baseline and cumulative change scope, the contract entry, and its
assigned review responsibility. Let it discover applicable topics and inspect
the actual files. Do not inherit the main agent's conversation, implementation
rationale, or compliance conclusions, and do not supply other reviewers'
conclusions. Reviewers may request missing task facts without adopting the
main agent's judgment.

All three reviewers work read-only. They may read files, diffs, relevant history,
callers, owners, and suitable reference implementations. They must not edit
files, run tests, builds, formatters, validators, or the application, make
commits, or launch further agents. Existing validation evidence can be examined
without treating it as work the reviewer executed.

Keep the finding scope on defects introduced or materially affected by this
task's cumulative changes. Read unchanged surrounding code when needed to
understand a changed boundary; this is not a request to audit or repair the
whole repository. On later rounds, examine the cumulative final change as well
as the corrections, rather than only the most recent patch.

Each reviewer reads the authority rules and project entry and respects relevant
project overrides. Assigned responsibilities focus the review without waiving
compatible requirements:

| Reviewer | Questions to examine |
| --- | --- |
| `pck_review_structure` | Do the changed responsibilities, interfaces, data flow, ownership, lifetimes, and failure behavior follow Consistency First, EIB, and suitable local precedents? |
| `pck_review_style` | Do changed prose, comments, examples, and delivery wording follow Direct Statements? Does changed code follow the applicable complete language profile and project style overrides? |
| `pck_review_project` | Which project topics apply to the changed responsibilities and consumers? Do the changes preserve their obligations, conditions, exceptions, authorization boundaries, and required validation evidence? |

For contract changes, assess the maintained requirements and navigation within
the same responsibilities. Use the pre-edit requirements and authorized
decisions to check preservation of meaning. If no project contract or language
profile applies, state that fact; still perform the role's remaining review.

Return concrete findings with the requirement or named section, file and
location, evidence of the violation, and its consequence. Separate confirmed
problems from questions requiring evidence or a user decision. State the scope
actually examined and any missing context or coverage. Report no findings only
after completing the assigned review; missing tools, a failed launch, an absent
response, or an unexamined responsibility is not a pass.

If the host cannot provide independent contexts, report the review incomplete.
Self-review does not fulfill the independent-review requirement.

## Resolve findings within three rounds

One round consists of all three reviews of the same file state and the main
agent's assessment of their results. Allow at most three review rounds for the
current task's changes. Corrections do not reset the count.

Collect the results before resuming edits. Judge findings against the actual
requirements and code evidence; agreement counts do not decide correctness.
The main agent has final authority over returned findings and recommendations
and may veto any of them. A veto removes that item as a review blocker and may
allow the review to be accepted without the proposed change. Resolve accepted
findings within the task's authority.

For every veto, tell the host which reviewer raised the item, the affected
requirement and location, what was proposed, why the main agent rejected it,
and the affected scope or remaining uncertainty. Make that disclosure before
or with the completion report. Identify an acceptance that relies on vetoes;
do not describe it as the reviewers having found no issues.

A veto decides the disposition of a returned review item. It does not replace
a missing independent review, change the governing requirements or exceptions,
or turn failed or unexecuted builds, tests, or runtime checks into passes.
Report those actual results separately. Do not change validation inputs merely
to dismiss a finding.

After corrections in round one or two, complete affected project validation
and request all three reviews again. Keep reviewer contexts separate from the
main agent's reasoning. Supply the current changes and necessary factual
decisions for the next round.

After round three, stop automatic corrections. Preserve the work and report
problems and disputes that the main agent has neither resolved nor vetoed, and
any incomplete reviews, for human assessment. Do not commit, push, or declare
the changes accepted while those items remain unresolved. Missing review
infrastructure also requires an honest incomplete result rather than repeated
attempts to manufacture a passing review.

## Complete the round

Before declaring this round complete, confirm that all three reviewers examined
the final content, findings are resolved or explicitly vetoed with disclosure
to the host, and the main agent has completed the applicable project validation.
Any subsequent content change requires another review within the same
three-round limit; if none remains, hand the unreviewed change to the user
without claiming completion.

Describe the changed scope, review rounds and actual models used, model
fallbacks, veto decisions, validation actually performed, and any remaining
problems or coverage limits in the delivery conversation. Keep review results
in the conversation; do not create PCK review histories, state files, or input
archives. Commits, pushes, and publication retain their existing authorization
requirements.
