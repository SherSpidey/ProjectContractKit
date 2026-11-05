# ProjectContractKit

ProjectContractKit (PCK) helps coding agents keep a project's responsibilities,
ownership, dependencies, and conventions coherent as its code grows. Its
contracts and Skills express the design decisions that should guide each change.

The portable package is [contract/](contract/README.md). It contains three core
Skills, language and platform Skills, optional Unity guidance, a task workflow
with independent reviews, and a Skill for maintaining project contracts. Project
requirements are written as Markdown topics.

## Use in a project

The core package contains the package entry, version, three core Skills,
`pck-workflow`, and `pck-maintain`. Copy that core package into the project's
`contract/` directory, then copy only the optional Skill directories the project
uses under `contract/skills/`. Inspect an existing destination before updating
it, and preserve the project's own contract content. The installed project's
PCK block records the selected optional Skill names; this is installation
metadata, not a copy of their rules or task content.

Add the following navigation to the project's agent instructions with the
authorization required by that project:

~~~markdown
<!-- BEGIN PCK -->
Read `contract/README.md` before editing project files. Follow its authority
and task-reading rules. Read all three core Skills, installed language and
platform Skills applicable to the task, and project topics. Use
`contract/skills/pck-maintain/SKILL.md` to create, convert, or maintain the
project contract.
Follow `contract/skills/pck-workflow/SKILL.md` from task start. Complete its
three independent reviews before declaring this round's changes complete.
After context compaction or summary-based resumption, complete the workflow's
context recovery before continuing.
Installed optional Skills:
<!-- Add one line such as `- \`cpp-style\`` per installed Skill; remove this comment when complete. -->
<!-- END PCK -->
~~~

Verify the core paths and every listed optional path after copying. The PCK block
in the project-root agent instruction file is the single
installation declaration; do not redefine the selected Skill set in nested
agent files. Each entry is a directory name under `contract/skills/`, whose
entry file is `contract/skills/<name>/SKILL.md`. Copy and list dependency Skills
together during installation. For example, Unity C# work includes C# Style, and
Unity shader work with embedded or associated HLSL includes HLSL Style. A
missing, unknown, or duplicate entry, or a missing declaration, makes the
installation incomplete. If a task reaches an unlisted responsibility, update
the installation under the project's existing authorization before editing.
Load an installed Skill only when the task reaches its language, platform, or
runtime responsibility.

Read the package guide and use
[pck-maintain](contract/skills/pck-maintain/SKILL.md) to express the project's
requirements. The installed project's `contract/project/README.md` holds its
shared requirements and links to any topic documents needed by its content.

Maintain one authoritative statement of each requirement. Keep related
conditions, exceptions, and examples together. Choose file boundaries from the
topics that agents need to understand and maintain together.

## Work with the contract

Read the core Skills and shared project requirements for each task. Load the
installed language and platform Skills applicable to the task and the project
topics before making decisions they govern. Follow related interfaces and
ownership into neighboring topics when the work reaches them.

Follow [pck-workflow](contract/skills/pck-workflow/SKILL.md) from task start
through the independent reviews of the completed changes. Its named review
assignments support host-specified models and autonomous model selection.
Apply the project's own build, execution, and review requirements to the actual
change.

Contract maintenance operates directly on the Markdown files. The agent
preserves meaning, resolves authorized decisions, and keeps navigation useful.
The package consists of documentation and Skills; its use requires file access
and an agent that can follow the instructions.
