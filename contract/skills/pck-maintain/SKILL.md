---
name: pck-maintain
description: Create, convert, amend, or reorganize a project's Markdown contract while preserving its meaning, scope, and useful detail.
---

# Maintain the Project Contract

Read [the package entry](../../README.md), the three core Skills, and the
existing project contract before changing its requirements. Use this Skill for
contract authoring and maintenance, including a request to input a contract.
The requested task defines the authorized changes.

Read [the contract writing guide](references/contract-writing.md) before
drafting or restructuring content. It supplies the writing standard, adaptable
entry and topic templates, a complete example, and finished-content requirements.

## Understand the intended requirements

Read the complete supplied material and applicable user decisions. Distinguish
requirements from recommendations, examples, explanations, and open questions.
Preserve owners, conditions, quantities, thresholds, prohibitions, exceptions,
approval boundaries, and any required validation behavior.

Retain useful reasons that explain a present invariant, such as ownership,
lifetime, numeric meaning, failure behavior, or an interface obligation.
Keep explicit non-goals when they define the responsibility's boundary.
Examples retain their stated scope; an example does not automatically create
a universal rule.

Reconcile the material with the current project contract and the package's
priority rules. Use decisions already supplied by the user. Ask about a
material contradiction or ambiguity that cannot be resolved from those
decisions. Continue independent work and describe any unresolved requirement
in the conversation without presenting it as settled policy.

## Write coherent topics

Use ordinary Markdown headings, paragraphs, lists, tables, and code examples
where they clarify meaning. Requirements can use direct words such as must,
must not, or prefer. Their wording establishes the intended obligation.

Keep conditions, exceptions, explanations, and examples with the requirements
they qualify. Include only the information that exists and helps application.
Choose a topic boundary from the requirements that need to be understood and
maintained together.

The installed project's `contract/project/README.md` contains shared project
requirements and navigation. A small contract can fit there. Create another
file when a real topic benefits from independent reading or maintenance.
Describe the topic's scope and link it from the project entry. Do not create
empty topics or prescribe a number of files, rules, headings, or lines.

Keep one authoritative location for each requirement. Link related topics
where their interaction matters. Identifiers are optional aids for referring
to the current contract. Project-specific conventions and exceptions belong
in project topics; the built-in language Skills remain reusable defaults.

A project Skill is useful for a recurring procedure that needs its own
instructions. Create one only when the project actually needs that procedure.
Keep it and its supporting files under `contract/project/`, and make it
reachable from the relevant topic.

## Change the contract directly

Add an authorized requirement to the topic that owns it. Refine an existing
requirement in place. Merge duplicates only when their meaning, scope,
conditions, and exceptions agree.

Delete or relax a requirement only when the requested change authorizes that
semantic change. An implementation that violates a requirement is not authority
to change it. Existing user authorization is sufficient within its scope.

Reorganize, split, merge, or rename topics as needed within an authorized
maintenance task while preserving meaning. Update affected links and navigation
in the same change. A reorganization does not itself authorize new requirements
or the removal of an obligation.

Keep user-designated protected files and external actions within their
authorization boundaries. When updating an installed package, preserve its
project-owned contract and resources.

## Keep inputs transient

Use supplied files and conversation content only for the current conversion.
The maintained project contract is the authoritative result and must be
understandable without its input material.

Do not copy, archive, or persist inputs or input-origin records. This includes
input filenames, hashes, source identifiers, clause mappings, source notes, and
copies in scratch files, logs, caches, or reports. Do not create `sources/`.
Put necessary meaning directly into the contract.

User-owned original files are outside PCK's automatic cleanup scope. Read them
where the user provides them. Contract maintenance does not authorize deleting
them.

## Finish the maintenance task

Compare the resulting contract with the supplied material during conversion.
Check semantic completeness, obligation strength, conditions, exceptions,
examples, and useful context. Perform this comparison as part of the work,
without persisting an input ledger.

Read changed topics together with their related requirements. Resolve duplicate
or contradictory statements, check links and navigation, and confirm that a
reader can determine which requirements apply. Preserve the distinction between
an example and an obligation.

Deliver the maintained files and describe the completed scope and any
unresolved decisions in the conversation. Keep the contract focused on current
requirements rather than task records or a history of its maintenance.
