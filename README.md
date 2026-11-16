# ProjectContractKit

ProjectContractKit (PCK) helps coding agents keep a project's responsibilities,
ownership, dependencies, and conventions coherent as its code grows. Its
contracts and Skills express the design decisions that should guide each change.

The portable package is [contract/](contract/README.md). Its core Skills provide
three design principles, a task workflow with independent reviews, and project
contract maintenance. Optional Skills provide language, platform, and tool
guidance, including Unity, Godot, and RenderDoc. Project requirements are Markdown
topics.

## Use in a project

The core package contains the package entry, version, and all Skill directories
and resources under `contract/skills/core/`: the three core principle Skills,
`pck-workflow`, and `pck-maintain`. Copy that core package into the project's
`contract/` directory. Copy only the optional Skill directories the project uses
from `contract/skills/optional/` into the same path in the project. Inspect an
existing destination before updating it, and preserve the project's own contract
content. The installed project's PCK block records the selected optional Skill
names; this is installation metadata, not a copy of their rules or task content.

During updates, retain the project's optional Skill selection. Relocate installed
Skill directories to their matching group and update agent and project references
while preserving project requirements.

Add the following navigation to the project's agent instructions with the
authorization required by that project:

~~~markdown
<!-- BEGIN PCK -->
Read `contract/README.md` before editing project files. Follow its authority
and task-reading rules. Read all three core principle Skills, installed optional
Skills applicable to the task, and project topics. Use
`contract/skills/core/pck-maintain/SKILL.md` to create, convert, or maintain the
project contract.
Follow `contract/skills/core/pck-workflow/SKILL.md` from task start through completion.
After context compaction or summary-based resumption, complete the workflow's
context recovery before continuing.
Installed optional Skills:
<!-- Add one line such as `- \`cpp-style\`` per installed Skill; remove this comment when complete. -->
<!-- END PCK -->
~~~

Verify the core paths and every listed optional path after copying. The PCK block
in the project-root agent instruction file is the single
installation declaration; do not redefine the selected Skill set in nested
agent files. Each optional entry is a directory name under
`contract/skills/optional/`, whose entry file is
`contract/skills/optional/<name>/SKILL.md`. Copy and list dependency Skills
together during installation. For example, Unity C# work includes C# Style, and
Unity shader work with embedded or associated HLSL includes HLSL Style. Godot
GDScript work includes Godot Development and GDScript Style; Godot C# work includes
Godot Development and C# Style. A missing, unknown, or duplicate entry, or a
missing declaration, makes the installation incomplete. If a task reaches an
unlisted responsibility, update the installation under the project's existing
authorization before editing.
Load an installed optional Skill only when the task reaches its language,
platform, tool, or runtime responsibility.

Read the package guide and use
[pck-maintain](contract/skills/core/pck-maintain/SKILL.md) to express the project's
requirements. The installed project's `contract/project/README.md` holds its
shared requirements and links to any topic documents needed by its content.

Maintain one authoritative statement of each requirement. Keep related
conditions, exceptions, and examples together. Choose file boundaries from the
topics that agents need to understand and maintain together.

## Work with the contract

Read the three core principle Skills and shared project requirements for each
task. Load the installed optional Skills applicable to the task and the project
topics before making decisions they govern. Follow related interfaces and
ownership into neighboring topics when the work reaches them.

Follow [pck-workflow](contract/skills/core/pck-workflow/SKILL.md) from task start
through completion. The main agent decides whether independent review is needed
and selects roles for the actual change. Review assignments support host-specified
models and autonomous selection. Apply the project's own validation and review
requirements.

Contract maintenance operates directly on the Markdown files. The agent
preserves meaning, resolves authorized decisions, and keeps navigation useful.
The package consists of documentation and Skills; its use requires file access
and an agent that can follow the instructions.
