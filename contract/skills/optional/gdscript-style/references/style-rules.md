# GDScript Writing Rules

Use Godot's [GDScript style guide](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html)
as defaults for new and intentionally changed code. Apply project decisions and
scoped exceptions first; preserve unrelated formatting. These rules target
GDScript in Godot 4; check features against the project's actual version.

## Names

| Declaration | Default |
| --- | --- |
| Files, functions, variables, and signals | `snake_case` |
| Classes, nodes, and enum types | `PascalCase` |
| Constants and enum values | `CONSTANT_CASE` |
| Internal functions, variables, and overridable hooks | A single leading `_` |

Name signals for completed events, such as `health_changed`. Preserve required
callback, external API, and serialized spellings. Use `PascalCase` for names
representing preloaded classes.

## Layout and expressions

Use tabs, UTF-8 without BOM, and LF with one final newline. Keep one statement per
line. Separate function and class definitions with two blank lines; separate
logical sections inside functions with one. Keep lines below 100 characters,
aiming below 80.

Indent ordinary continuation lines twice; arrays, dictionaries, and enums once.
Keep trailing commas in multiline arrays, dictionaries, and enums. Prefer `and`,
`or`, and `not`. Use spacing and parentheses to clarify expressions.

## Declaration order

Follow the guide's order: script annotations, `class_name`, `extends`, class
documentation; signals, enums, constants, static fields, exports, ordinary
fields, and `@onready` fields; static initialization and methods, built-in and
custom overrides, other methods, and inner classes. Within applicable groups,
place public before internal members. Preserve initialization dependencies.
Keep locals near first use.

## Types and conversions

Follow the project's static-typing policy. Express parameter, return, and
important data-boundary types clearly. When using typed declarations, prefer
`:=` when the right side spells out the type; write an explicit type when type
or numeric intent is ambiguous. For example:

```gdscript
var direction := Vector3(1.0, 0.0, 0.0)
var health: int = 0
```

Check the actual declared return type when inferring from calls or node lookups.
Use typed collections supported by the target version. Keep `Variant` where a
dynamic boundary requires it. Full static typing remains a project choice.

Follow the [static typing reference](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/static_typing.html)
for conversions. An object cast with `as` can silently produce `null` on a type
mismatch; use it when that result is intended and handled. Use type checks or
typed assignment when a mismatch should be detected. Safe-line highlighting
does not establish object validity or runtime correctness.

## Comments and diagnostics

Use `#` for ordinary comments and
[`##` documentation comments](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_documentation_comments.html)
for useful API and property documentation. Place member documentation immediately
before its declaration or annotations; exported-property documentation also
supplies Inspector tooltips. State conditions, units, ownership, and useful limits.

Use the project's [warning policy](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/warning_system.html).
Keep warning suppressions specific, scoped, and justified. Global warning
severity and mandatory typing are project choices.

Keep [assertion expressions](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_basics.html#assert-keyword)
free of side effects. Release builds omit assertions, so required input and
runtime validation must execute independently of them.
