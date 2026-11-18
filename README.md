# ProjectContractKit

ProjectContractKit (PCK) helps coding agents keep a project's responsibilities,
ownership, dependencies, and conventions coherent as its code grows. Its
contracts and Skills express the design decisions that should guide each change.

The portable package is [contract/](contract/README.md). Its core Skills provide
three design principles, a task workflow, and project contract maintenance.
Optional Skills provide language, platform, and tool guidance, including Unity,
Godot, and RenderDoc. Project requirements are Markdown topics.

## Use in a project

Copy the [core package](contract/README.md#installation) into the project's
`contract/` directory. Copy the selected optional Skill directories from
`contract/skills/optional/` into the same path in the project.

Inspect an existing destination before updating it. Preserve the project's own
contract and optional Skill selection. Where directory layouts differ, relocate
the installed Skills and update their references.

Add the following block to the project-root agent instruction file with the
authorization required by that project:

~~~markdown
<!-- BEGIN PCK -->
Read `contract/README.md` before editing and follow its authority and task-reading
rules. Follow `contract/skills/core/pck-workflow/SKILL.md` for changes and context
recovery. Use `contract/skills/core/pck-maintain/SKILL.md` for contract work.
Installed optional Skills:
<!-- List selected Skill directory names as bullets. Remove this comment. -->
<!-- END PCK -->
~~~

Copy and list dependency Skills together. For example, Godot GDScript work
includes `godot-development` and `gdscript-style`. Check the installed paths and
root block against the [installation requirements](contract/README.md#installation).

## Work with the contract

Use [the package entry](contract/README.md#read-for-the-task) to select the
requirements and procedures for a change. The
[workflow](contract/skills/core/pck-workflow/SKILL.md) governs source review,
validation, and handoff. Use [pck-maintain](contract/skills/core/pck-maintain/SKILL.md)
for contract work. The project's shared requirements and topic links live in
`contract/project/README.md` when the project has its own contract.
