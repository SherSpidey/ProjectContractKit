# C++ Writing Rules

Apply these defaults to new and intentionally changed C++ code. Preserve
unrelated formatting. The project's agreed requirements and scoped exceptions
take priority.

Use the code's names, types, qualifiers, and layout to make declaration roles,
ownership, reading order, and interface obligations understandable.

## Names and declaration roles

| Declaration | Naming form |
| --- | --- |
| Classes, structs, other types, enums, and concepts | `PascalCase` |
| Enumerators, functions, methods, constructors, and destructors | `PascalCase` |
| Local variables, parameters, and public or protected non-static members | `snake_case` |
| Private non-static data members | `snake_case_` |
| Static objects and static data members at any access level | `PascalCase` |
| `constexpr` values, compile-time tables, and template metadata | `PascalCase` |
| Template parameters, aliases, and type-level vocabulary | `PascalCase` |
| Macros and include guards | The project's established all-capital form |

Classify static and compile-time declarations before choosing a local-variable
or instance-member form. A private static member uses `PascalCase`; a private
instance data member uses the trailing underscore.

Treat acronyms as units and keep their spelling consistent across related
names. Preserve established forms such as `InvPI`, `BufferSize`, and
`CStrAffixes` in declarations, definitions, derived names, and callers.
Required external spellings remain exact.

## Types, state, and ownership

Use an aggregate when its visible fields form the data contract and direct
access serves its callers. Declare one logical member per line, group related
members, and give fields meaningful defaults where those defaults exist.

Use `class` by default for a type that owns invariants, resource lifetime,
synchronization, or controlled mutation. A project can choose `struct` for
those same responsibilities. Express access, ownership, and mutation boundaries
clearly in either form.

Constructors, conversions, and member functions serve concrete invariants or
operations. Distinguish identity, primary state, derived values, caches, and
ownership state in the type's organization. Keep the facts and the results
maintained from them understandable.

## Expressions and guarantees

| Intended use | Declaration form |
| --- | --- |
| Read-only value whose initializer makes the type clear | `const auto` |
| Mutable value whose initializer makes the type clear | `auto` |
| Borrowed mutable object | `auto&` |
| Borrowed read-only object | `const auto&` |
| Public interface, narrowing boundary, ABI value, or unclear numeric meaning | An explicit type |

Type deduction must preserve the intended type, constness, reference category,
and ownership. Write an explicit type when deduction hides a conversion,
range, ABI detail, or numeric interpretation. Keep required references and
const qualifiers.

Use explicit casts for intentional numeric, pointer, and enum conversions.
Declare `noexcept` only when the operation's complete implementation provides
that guarantee.

## Files and dependencies

Use the established project title and file-header convention. Resolve a missing
convention through suitable local evidence or a project decision before adding
boilerplate.

Follow the established include-guard form. Group includes by purpose and put one
blank line between real groups. Preserve the project's order for standard,
library, feature, and current-header includes. Include direct dependencies
explicitly.

Keep definitions in declaration order and related overloads together.
`using namespace` directives belong only in implementation translation units,
such as `.cpp`, `.cc`, and `.cxx`. Use explicit namespace qualification in
public headers, private headers, and shared inline files.

## Layout

### Braces

Use Allman layout for functions, types, and control flow: place the opening
brace on its own line. Align `else` and `catch` with the closing brace that
introduces them.

### Signatures and calls

Keep a short signature or call on one line. When wrapping, keep the first
parameter or argument on the line containing the function name and opening
parenthesis. Place each remaining parameter or argument on its own
continuation line. Put closing punctuation on the last parameter or argument
line.

~~~cpp
void CopyVisibleRange(const BufferView& source,
    Buffer& destination,
    const Range& visible_range)
{
    destination.Copy(source, visible_range);
}
~~~

### Conditions

Keep short conditions on one line. Wrap a condition when its full expression
cannot be read comfortably on one line. Put each continued logical operator at
the end of the preceding line. Use consistent continuation indentation for
comparisons and Boolean expressions.

~~~cpp
if (has_valid_input &&
    matches_required_layout &&
    preserves_expected_precision)
{
    ProcessInput();
}
~~~

### Spacing and control flow

Separate real changes of purpose, data stage, or ownership with a blank line.
Keep the statements of one operation together. A short guard or return can stay
compact when it is one operation. Wrapping an expression does not create an
additional responsibility.

## Interfaces and annotations

Keep declarations and definitions consistent in spelling, qualifiers,
visibility, and ownership. Public signatures express the interface and its
obligations without incidental implementation detail.

Use attributes for required compiler, ABI, or diagnostic behavior. Make
visibility and lifetime obligations clear where values, pointers, references,
or ownership cross a boundary.

## Comments

Explain facts that cannot reliably be recovered from the code: numeric
assumptions, ownership, lifetime, ABI constraints, ordering requirements, and
non-obvious algorithmic decisions. Place the explanation next to the invariant.

Comments state current behavior and obligations. Apply
[direct-statements](../../direct-statements/SKILL.md) to comments and examples.
Avoid a comment that only restates the following instruction.

## Exceptions and review

Preserve external API names, compiler-required spellings, generated regions,
and public compatibility names. Make an exception clear at its owning boundary
and in the relevant project requirement or review explanation. A recurring
exception belongs in an explicit project requirement.

Examine all applicable naming families, member roles, qualifiers, dependency
groups, layout forms, interface annotations, and comments. Read the
implementation to assess semantic guarantees such as ownership and failure
behavior.
