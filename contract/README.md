# Project contract

PCK combines design principles, language defaults, and the project's agreed
requirements. `VERSION` identifies the portable package release.

## Authority

Platform instructions, applicable user decisions, and project permissions
govern the work. Apply the three core Skills together:

| Skill | Responsibility |
| --- | --- |
| [everything-is-block](skills/everything-is-block/SKILL.md) | Make responsibility, data flow, ownership, and lifetime visible. |
| [consistency-first](skills/consistency-first/SKILL.md) | Ground requirement application and open choices in suitable project evidence. |
| [direct-statements](skills/direct-statements/SKILL.md) | State current facts and requirements directly. |

Consistency First is the shared method for applying all Skills and project
requirements; each retains its own obligations and scope. This execution role
does not give it higher authority. For project choices, apply agreed requirements
and scoped exceptions, then their selected project Skills, then built-in language defaults.
Keep compatible obligations in force. Local code illustrates application and
guides open choices; it does not waive requirements. Resolve material conflicts
through applicable user decisions or obtain the missing decision before changing
the requirement.

## Read for the task

Read this entry, all three core Skills, and the full `project/README.md` when
present. Read complete applicable topics, profiles, and references, including
their conditions, exceptions, and examples. Select them by responsibilities,
interfaces, owners, and consumers as well as paths; follow necessary links and
expand the reading when scope or applicability changes.

| Work | Required procedure or profile |
| --- | --- |
| Changes to any files | [pck-workflow](skills/pck-workflow/SKILL.md), from task start through independent review |
| Contract creation or maintenance | [pck-maintain](skills/pck-maintain/SKILL.md) |
| C++ | [cpp-style](skills/cpp-style/SKILL.md) and its full rule reference |
| HLSL | [hlsl-style](skills/hlsl-style/SKILL.md) and its full rule reference |

Choose language profiles by actual language and role, including shared
extensions. Use a project profile for other languages. After compaction or
summary-based resumption, complete [context recovery](skills/pck-workflow/SKILL.md#recover-context).

## Project content

`project/README.md` owns shared requirements and topic navigation. Keep each
requirement in one authoritative location, with its conditions and exceptions.
Keep project conventions, Skills, and supporting resources under `project/`;
create topics and procedures only when their responsibilities need them.
Without a project contract, use applicable user decisions, project instructions,
and built-in defaults.

Contract changes require authorization. Contract conformance is judged from
source and independent review; static contract checkers, adapters, rule mappings,
and generated example suites are not required. The project owns its separate
build, test, and runtime validation obligations.
