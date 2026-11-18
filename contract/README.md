# Project contract

PCK combines design principles, language and platform defaults, and the project's
agreed requirements. `VERSION` identifies the portable package release.

## Authority

Platform instructions, applicable user decisions, and project permissions
govern the work. Contract changes require authorization. Apply the following
three core principle Skills, every applicable project requirement, and the
applicable installed optional Skills to each change.

| Skill | Responsibility |
| --- | --- |
| [everything-is-block](skills/core/everything-is-block/SKILL.md) | Make responsibility, data flow, ownership, and lifetime visible. |
| [consistency-first](skills/core/consistency-first/SKILL.md) | Ground requirement application and open choices in suitable project evidence. |
| [direct-statements](skills/core/direct-statements/SKILL.md) | State current facts and requirements directly. |

Consistency First is the shared method for applying all Skills and project
requirements; each retains its own obligations and scope. This execution role
does not give it higher authority. For project choices, apply agreed requirements
and scoped exceptions, then their selected project Skills, then built-in language
and platform defaults.

Keep compatible obligations in force. Local code illustrates application and
guides open choices; it does not waive requirements. Resolve material conflicts
through applicable user decisions or obtain the missing decision before changing
the requirement.

## Installation

The always-installed core package contains this entry, `VERSION`, and all Skill
directories and resources under `skills/core/`: the three core principle Skills,
`pck-workflow`, and `pck-maintain`. Optional Skills live under `skills/optional/`.

For an installed project, select optional Skills by responsibility. Record the
selection in one PCK block in the project-root agent instruction file. That
block is the only activation declaration. A complete installation has every
core file and one well-formed block. Entries are unique, known directory names
under `contract/skills/optional/` with an installed `SKILL.md`.

Correct an incomplete installation before editing. If the task reaches a
responsibility that requires an unlisted Skill, install and declare it and its
dependencies before editing. Use the project's existing authorization for
installation changes.

When maintaining PCK itself, use its repository instructions and package contents
to determine available Skills.

## Read for the task

Read this entry, all three core principle Skills, and the full
`project/README.md` when present. Read the applicable procedures, active optional
Skills, and project topics in full, including their references and examples.
Follow any stated conditions for reading a reference. Select by responsibilities,
interfaces, owners, consumers, and paths. Use the actual language, platform,
tool, and runtime, including for embedded code and shared extensions.

Follow necessary links. Reuse current originals already read in your context.
Expand or refresh affected reading when scope, applicability, or source changes.

| Work | Required procedure or optional Skill |
| --- | --- |
| Changes to any files | [pck-workflow](skills/core/pck-workflow/SKILL.md), from task start through completion |
| Contract creation or maintenance | [pck-maintain](skills/core/pck-maintain/SKILL.md) |
| RenderDoc terminal capture, inspection, or image export | `skills/optional/renderdoc-cmd/SKILL.md` |
| C++ source | `skills/optional/cpp-style/SKILL.md` |
| C# source | `skills/optional/csharp-style/SKILL.md` |
| GDScript source | `skills/optional/gdscript-style/SKILL.md` |
| HLSL source or shader stages | `skills/optional/hlsl-style/SKILL.md` |
| ShaderLab or associated Unity HLSL | `skills/optional/shaderlab-style/SKILL.md`. Embedded or associated HLSL also requires HLSL Style with the stated Unity exceptions. |
| Unity APIs, serialized data, assets, or Editor operations | `skills/optional/unity-development/SKILL.md`. Unity C# source also requires C# Style. |
| Godot APIs, scenes, resources, serialized data, or Editor operations | `skills/optional/godot-development/SKILL.md`. Godot GDScript source also requires GDScript Style. Godot C# source also requires C# Style. |

Use a project Skill for other languages or platforms. After compaction or
summary-based resumption, complete
[context recovery](skills/core/pck-workflow/SKILL.md#recover-context).

## Project content

`project/README.md` owns shared requirements and topic navigation. Keep each
requirement in one authoritative location, with its conditions and exceptions.
Keep project conventions, Skills, and supporting resources under `project/`;
create topics, procedures, or project Skills only for responsibilities that need
separate treatment.
Without a project contract, use applicable user decisions, project instructions,
and built-in defaults.
