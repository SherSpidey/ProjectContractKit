---
name: pck-workflow
description: Apply the project contract to changes, review affected source, and establish validation and acceptance status.
---

# Work with the Project Contract

Use this workflow for changes to code, documentation, configuration, or the
contract. Discussion and read-only reviews use the applicable requirements
within their assigned scope.

## Prepare the change

Follow applicable agent instructions and [the package entry](../../../README.md)
before editing.

Define the authorized scope, observable outcome, and evidence of success.
Identify affected responsibilities, owners, data flow, lifetimes, interfaces,
and failure boundaries. Apply
[Consistency First](../consistency-first/SKILL.md) to the decisions and causes
the change must address.

Follow project branch policy and set the task baseline. Track its cumulative
changes across commits, uncommitted edits, additions, moves, and deletions.
Keep that diff scoped to the task.

## Apply and self-review

Implement complete responsibility units with their governing clauses and
exceptions at hand.

Review complete affected units identified by the cumulative diff. Use the
final source and consult the baseline for removals. Follow dependencies and
consumers far enough to verify affected interfaces and behavior. Match review
depth to the change's reach and risk.

In the same self-review, check each core principle and every applicable project
and optional Skill requirement. Check local EIB boundaries separately from
ownership and failure behavior. Use actual declarations and expressions for
language rules and numbered original lines when layout matters.

## Validation and acceptance

Follow project and task requirements for checks, evidence, and ownership. Where
ownership is unspecified, the main agent runs required builds, static checks,
and automated tests, and a human performs any needed runtime acceptance such
as gameplay, rendering, or interactive Editor behavior.

## Independent review

When the project or task requires independent review, or when a material risk
or open question warrants a second assessment, read and follow the
[independent review procedure](references/independent-review.md).

## Resolve and hand off

Resolve findings against the governing requirements. Correct the affected
responsibility together with the consumers it changes.

After a correction, recheck affected units and conclusions, repeat affected
agent checks, and mark affected manual checks as pending. Reuse evidence
that still applies to the final source, configuration, and tools.

Report implementation as ready after final self-review, selected reviews, and
required agent checks are complete, with findings resolved or openly vetoed.
Report review coverage, validation results, and material limits in the
conversation. Do not create PCK state files or review histories.

Report acceptance separately from implementation readiness. Confirm it when
all applicable required checks pass based on results from their assigned
owners. For pending human checks, give the setup or entry point, steps, and
expected observation.

Resolve open findings and required review gaps before claiming acceptance or
publishing. Publishing also requires authorization and satisfaction of any
release gates.

## Recover context

After compaction or summary-based resumption, every agent follows the
[context recovery procedure](references/context-recovery.md) before continuing.
