# Writing Project Contracts

Write the decision or behavior an agent must apply. Use direct wording that
preserves the difference between an obligation, prohibition, preference, and
permission. Keep scope, conditions, limits, exceptions, and useful reasons
beside the requirement. An example illustrates its stated scope.

A paragraph may contain several obligations; retain each and its qualifiers.
State owners, dependencies, lifetimes, interfaces, failure behavior, numeric
limits, and validation duties wherever the requirement depends on them.
An exception identifies its condition and required behavior, not a general waiver.

## Organization

Use `contract/project/README.md` for shared requirements and topic navigation.
Identify any topic required for every task. A small contract can remain in this
entry; create a topic when its related requirements need independent treatment.

Give topics descriptive titles and group decisions that must be understood
together. Keep each requirement authoritative in one place and link related
topics. Use headings, paragraphs, lists, tables, or examples only where they
clarify the content; omit empty sections and template-driven filler.

Keep the entry and core procedures concise. Remove repetition and generic advice;
retain detail that changes a decision or is necessary to apply a requirement.
Project exceptions name the affected default and their scope.

## Finished text

A reader can find the applicable requirements, understand their qualifiers and
related decisions, and distinguish current capabilities from required work.
Names, paths, commands, and interfaces agree with the project. The contract is
usable without its input material; reorganization preserves meaning and links.
