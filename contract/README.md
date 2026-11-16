# Project contract

PCK combines design principles, language and platform defaults, and the project's
agreed requirements. `VERSION` identifies the portable package release.

## Authority

Platform instructions, applicable user decisions, and project permissions
govern the work. Apply the three core principle Skills together:

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

## Read for the task

Read this entry, all three core principle Skills, and the full
`project/README.md` when present. Read complete applicable topics, Skills, their
references, and examples, including their conditions and exceptions. Select them
by responsibilities, interfaces, owners, and consumers as well as paths; follow
necessary links and expand the reading when scope or applicability changes.

The always-installed core package contains this entry, `VERSION`, and all Skill
directories and resources under `skills/core/`: the three core principle Skills,
`pck-workflow`, and `pck-maintain`. Optional Skills live under `skills/optional/`.
Select them by responsibility during installation and record their names in the
PCK block of the project-root agent instruction file. The block is the activation
set for optional Skills: each entry is a directory name under
`contract/skills/optional/`, its `SKILL.md` must exist, and an unlisted optional
directory is not loaded. A missing core file, missing or unknown listed optional
Skill, duplicate entry, or missing block makes the installation incomplete. If a
task reaches an unlisted responsibility, update the installation and its
dependencies under the project's existing authorization before editing.

| Work | Required procedure or optional Skill |
| --- | --- |
| Changes to any files | [pck-workflow](skills/core/pck-workflow/SKILL.md), from task start through completion |
| Contract creation or maintenance | [pck-maintain](skills/core/pck-maintain/SKILL.md) |
| RenderDoc terminal capture, inspection, or image export | `skills/optional/renderdoc-cmd/SKILL.md` when installed. |
| C++ | `skills/optional/cpp-style/SKILL.md` when installed and C++ source is in scope. |
| C# | `skills/optional/csharp-style/SKILL.md` when installed and C# source is in scope. |
| GDScript | `skills/optional/gdscript-style/SKILL.md` when installed and GDScript source is in scope. |
| HLSL | `skills/optional/hlsl-style/SKILL.md` when installed and HLSL source or stages are in scope. |
| ShaderLab or associated Unity HLSL | `skills/optional/shaderlab-style/SKILL.md` when installed; embedded or associated HLSL also requires HLSL Style. |
| Unity APIs, serialized data, assets, or Editor operations | `skills/optional/unity-development/SKILL.md` when installed; Unity C# source also requires C# Style. |
| Godot APIs, scenes, resources, serialized data, or Editor operations | `skills/optional/godot-development/SKILL.md` when installed; Godot GDScript source also requires GDScript Style, and Godot C# source also requires C# Style. |

Choose installed optional Skills by actual language, platform, tool,
responsibility, and runtime, including embedded code and shared extensions.
Unity shader guidance supplies its stated exceptions to HLSL defaults. Use a
project Skill for other languages or platforms. After compaction or summary-based
resumption, complete [context recovery](skills/core/pck-workflow/SKILL.md#recover-context).

## Project content

`project/README.md` owns shared requirements and topic navigation. Keep each
requirement in one authoritative location, with its conditions and exceptions.
Keep project conventions, Skills, and supporting resources under `project/`;
create topics and procedures only when their responsibilities need them.
Without a project contract, use applicable user decisions, project instructions,
and built-in defaults.

Contract changes require authorization. Contract conformance is judged from
source, main-agent self-review, and independent review when needed; static
contract checkers, adapters, rule mappings, and generated example suites are not
required. The project owns its separate build, test, and runtime validation
obligations.
