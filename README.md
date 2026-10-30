# ProjectContractKit

ProjectContractKit (PCK) helps coding agents keep a project's responsibilities,
ownership, dependencies, and conventions coherent as its code grows. Its
contracts and Skills express the design decisions that should guide each change.

The portable package is [contract/](contract/README.md). It contains three core
Skills, complete C++ and HLSL writing profiles, a task workflow with independent
reviews, and a Skill for maintaining project contracts. Project requirements
are written as Markdown topics.

## Use in a project

Copy `contract/` into the project root. Inspect an existing destination before
updating it, and preserve the project's own contract content.

Add the following navigation to the project's agent instructions with the
authorization required by that project:

~~~markdown
<!-- BEGIN PCK -->
Read `contract/README.md` before editing project files. Follow its authority
and task-reading rules. Read all three core Skills and the applicable language
profile and project topics. Use `contract/skills/pck-maintain/SKILL.md` to
create, convert, or maintain the project contract.
Follow `contract/skills/pck-workflow/SKILL.md` from task start. Complete its
three independent reviews before declaring this round's changes complete.
<!-- END PCK -->
~~~

Read the package guide and use
[pck-maintain](contract/skills/pck-maintain/SKILL.md) to express the project's
requirements. The installed project's `contract/project/README.md` holds its
shared requirements and links to any topic documents needed by its content.

Maintain one authoritative statement of each requirement. Keep related
conditions, exceptions, and examples together. Choose file boundaries from the
topics that agents need to understand and maintain together.

## Work with the contract

Read the core Skills and shared project requirements for each task. Load the
applicable language profile and project topics before making decisions they
govern. Follow related interfaces and ownership into neighboring topics when
the work reaches them.

Follow [pck-workflow](contract/skills/pck-workflow/SKILL.md) from task start
through the independent reviews of the completed changes. Its named review
assignments support host-specified models and autonomous model selection.
Apply the project's own build, execution, and review requirements to the actual
change.

Contract maintenance operates directly on the Markdown files. The agent
preserves meaning, resolves authorized decisions, and keeps navigation useful.
The package consists of documentation and Skills; its use requires file access
and an agent that can follow the instructions.
