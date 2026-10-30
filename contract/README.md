# Project contract

Read this entry before working with the project's code or contract. PCK guides
design decisions through core Skills, language profiles, and the project's own
Markdown requirements.

For a task that changes files, follow
[pck-workflow](skills/pck-workflow/SKILL.md) from task start through the three
independent reviews required before declaring this round complete.

`VERSION` identifies the portable package release. The host project maintains
its own contract revisions independently.

## Authority

Platform instructions and the user's authorized decisions govern all work.
Project permissions continue to apply to protected files, external actions,
and publishing.

Apply the three core Skills together:

| Skill | Responsibility |
| --- | --- |
| [everything-is-block](skills/everything-is-block/SKILL.md) | Keep responsibility, data flow, ownership, and lifetime visible at every code boundary. |
| [consistency-first](skills/consistency-first/SKILL.md) | Ground open implementation choices in suitable project evidence and resolve important design decisions. |
| [direct-statements](skills/direct-statements/SKILL.md) | Express current facts and requirements without version comparisons or reconstruction narratives. |

`consistency-first` and `direct-statements` have equal priority. The core Skills
apply together across implementation and contract maintenance. They govern how
work is performed; project requirements supply concrete decisions within their
scope. [pck-workflow](skills/pck-workflow/SKILL.md) governs task execution and
independent final review. For contract work, `pck-maintain` governs the
maintenance procedure.

For a particular project decision, apply:

1. The project's agreed requirements and explicit exceptions within their scope.
2. The project-specific Skills and references those requirements select.
3. The applicable built-in language defaults.

A project preference for `struct` takes priority over the C++ default for
behavior-owning types. That preference leaves ownership and lifetime obligations
in effect. Keep project preferences in the project contract. Apply every other
compatible requirement.

Local code is evidence for choices the contract leaves open. Apply explicit
user decisions within their scope to resolve a conflict involving a core Skill,
the maintenance procedure, or project requirements. A project convention does
not silently waive a core principle or authorize a contract change. Ask for an
unresolved material decision before changing the governed requirement.

## Read for the task

Read all three core Skills. If `project/README.md` exists, read it in full: it
contains the project's shared requirements and navigation to its topics. Read
the complete applicable topics, including their conditions, exceptions, and
examples.

Select topics from the task's responsibilities, affected interfaces, owners,
and consumers as well as its file paths. Follow a relevant link when the
referenced material is needed to understand the requirement. Read more of the
contract when its applicability is uncertain. Revisit the selection when the
change reaches another responsibility or interface.

| Language | Profile |
| --- | --- |
| C++ headers, sources, templates, and inline files | [cpp-style](skills/cpp-style/SKILL.md) and its complete rule reference |
| HLSL shaders and shared shader includes | [hlsl-style](skills/hlsl-style/SKILL.md) and its complete rule reference |

Choose a profile from the file's actual language and role. Shared extensions
such as `.h` need the surrounding toolchain and callers to establish that role.
Read a project-provided profile when working in another language.

During implementation, preserve the established owner and failure behavior.
Examine the final change for duplicated responsibilities, unnecessary layers,
extra ownership paths, and inconsistent interfaces. Carry out the project's
own validation requirements and describe the actual result. The host project
owns its build, execution, review, and checker requirements. Contract authoring
and implementing project checkers are separately authorized tasks.

## Project content

The installed project's `project/README.md` is its contract entry. Keep shared
requirements there and link to any topic files with a short explanation of when
they apply. Create files for real topics; keep related rules, conditions,
exceptions, and examples together.

Each requirement has one authoritative location. Links connect related topics
without duplicating their rules. Keep project-owned Skills and supporting
files under `project/`. Add a Skill when a reusable procedure needs one, and
link it from the relevant project topic.

When no project contract exists, use the user's decisions, existing project
instructions, and the built-in defaults. Create project requirements through
an authorized contract-maintenance task.

Use [pck-maintain](skills/pck-maintain/SKILL.md) to create, convert, add, remove,
or reorganize contract content. Changes to requirements follow the user's
authorization. Ordinary implementation work does not silently change its
governing contract.

Before declaring this round's changes complete, finish the independent reviews
and completion checks in [pck-workflow](skills/pck-workflow/SKILL.md).
