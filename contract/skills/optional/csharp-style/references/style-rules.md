# C# Writing Rules

Use Microsoft's [C# conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
and [identifier conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names)
as defaults for new and intentionally changed code. Apply project decisions
and scoped exceptions first; preserve unrelated formatting.

## Names

| Declaration | Default |
| --- | --- |
| Namespaces, types, methods, properties, events, and constants | `PascalCase` |
| Interfaces | `I` followed by `PascalCase` |
| Type parameters | Descriptive `T`-prefixed names, or `T` for one clear role |
| Parameters and local variables | `camelCase` |
| Private instance fields | `_camelCase` |
| Private static fields | `s_camelCase` |

Choose descriptive identifiers and preserve required override, interface,
external API, and serialized spellings. Use C# keywords such as `int` and
`string` for their built-in types.

## Layout

Use four spaces for indentation and Allman braces. Keep one statement and
one declaration per line. Use braces for control-flow bodies. Separate methods
and real operation boundaries with blank lines.

Put `using` directives outside the namespace, with `System` namespaces first.
Keep established project grouping and wrapping. Place attributes on separate
lines above their declarations. Make member accessibility explicit.

## Expressions and comments

Use `var` when the initializer makes the type apparent, and explicit types
when it does not. Use parentheses to clarify compound expressions. Use
interpolation for readable string composition and `&&`/`||` for Boolean
short-circuit conditions where that behavior is intended.

Place useful comments before the code they explain. Use `//` for ordinary
comments and XML documentation for API contracts that need documentation.
Comments state the relevant condition or behavior rather than narrating syntax.

## Target compatibility

Use language features and library APIs supported by the actual target.
Namespace syntax, nullable annotations, and newer expressions must fit that
compiler and project configuration. Preserve platform-required fields,
attributes, callbacks, and serialization behavior; style changes do not
authorize interface or data migrations.
