# HLSL Writing Rules

Apply these defaults to new and intentionally changed shader code. Preserve
unrelated formatting. The project's agreed requirements and scoped exceptions
take priority.

Make user-defined roles, stage data flow, numeric meaning, coordinate spaces,
precision, packing, and interface obligations visible. Keep the path from stage
input to stage output understandable.

## Names and shader roles

| Declaration | Naming form |
| --- | --- |
| User-defined structs, functions, entry points, and named data types | `PascalCase` |
| Local variables, parameters, fields, and temporaries | `snake_case` |
| Compile-time constants | `PascalCase` |
| Mathematical constants | Stable forms such as `PI` and `InvPI` |
| Resources and samplers | The established binding-family form |
| Semantics, registers, and system values | Exact interface spelling |

Classify compile-time constants separately from ordinary variables. Treat an
acronym as a unit, and keep its spelling consistent across related names.
Maintain a role's spelling from its declaration through derived names and all
consuming stages. Preserve required language and system identifier spellings.

## Data and stage interfaces

Declare one logical field per line and preserve interface field order. Make
scalar, vector, and matrix types explicit at boundaries. Put a semantic on
the declaration that owns the stage interface. State resource classes and
register assignments explicitly wherever the interface requires them.

Distinguish input data, transformed data, sampled data, and stage output.
Construct an output near the point at which all its fields are valid.
The stage's data declarations express its actual input and output obligations.

## Numeric meaning

### Literals and conversions

Use `f` for a literal intended as `float` and `u` for one intended as `uint`.
For another numeric type, choose a supported suffix or explicit conversion
that preserves its intended precision. Select syntax supported by the
project's HLSL compiler, language mode, and enabled types. A literal requiring
another type must not be forced to `float`.

Use explicit casts for intentional conversions between scalar, vector,
integer, and matrix domains. Preserve the numeric interpretation, precision,
and packing required by the interface.

### Coordinate changes

State coordinate spaces, handedness, depth ranges, and matrix order at the
boundaries that change them. Make the input and output conventions of a
transformation clear to its consumers.

### Constrained arithmetic

Use `precise` when a numeric invariant requires restrictions on reordering,
fusion, or unsafe optimization. The qualifier constrains calculations
contributing to the qualified result. An operation that merely consumes that
result does not automatically inherit those restrictions.

Place `precise` at the result boundary that needs the invariant and explain
the requirement beside the calculation. Check the project's compiler and
target behavior. The qualifier does not promise identical results across
different hardware, compiler settings, or algorithms.

Consult Microsoft's [variable syntax reference](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-variable-syntax)
and [literal grammar](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl-appendix-grammar)
for language details. The actual project toolchain determines the supported
behavior.

## Files and dependencies

Use the established project title and file-header convention. Resolve a missing
convention from suitable local evidence or a project decision before adding
boilerplate.

Put shared declarations, reusable calculations, and entry points with the
responsibilities that own them. In a shader tree using that division, use
`.hlsli` for shared declarations and helpers and `.hlsl` for entry points.
Keep each entry-point file focused on its stage. Place reusable operations
beside the declarations that own their data.

Group includes by purpose and separate real groups with one blank line.
Keep include guards and declaration order consistent across the shader tree.

## Layout

### Braces

Use Allman layout for functions, structs, and control flow: place the opening
brace on its own line. Align `else` with the closing brace that introduces it.

### Signatures and calls

Keep a short signature or call on one line. When wrapping, keep the first
parameter or argument on the line containing the function name and opening
parenthesis. Place each remaining parameter or argument on its own
continuation line. Put closing punctuation on the last parameter or argument
line.

~~~hlsl
float3 EvaluateSurfaceLighting(float3 normal_ws,
    float3 light_direction_ws,
    float3 light_color)
{
    return saturate(dot(normal_ws, light_direction_ws)) * light_color;
}
~~~

### Conditions

Keep short conditions on one line. Wrap a condition when its full expression
cannot be read comfortably on one line. Put each continued logical operator at
the end of the preceding line. Use consistent continuation indentation for
chained predicates.

~~~hlsl
if (has_valid_surface &&
    matches_required_space &&
    alpha_mask > alpha_cutoff)
{
    StoreSurface();
}
~~~

### Spacing and stage flow

Use a blank line at actual transitions between input acquisition, coordinate
work, sampling, lighting, geometry, output construction, or stage rejection.
Keep one stage's tightly related statements together. A short helper can stay
compact when it performs one coherent operation. Wrapping an expression does
not introduce another stage.

## Interfaces and directives

Place entry-point attributes and thread-group declarations beside the entry
point they configure. Keep semantic and register spellings exact at interface
boundaries. Align resource and sampler names with their binding family.

Declare stage inputs and outputs explicitly. Compilation success does not
establish a missing interface. Inspect bindings, stage compatibility,
coordinate conventions, and numeric behavior according to the project's
actual validation requirements.

## Comments

Explain numeric limits, coordinate conventions, packing, temporary lifetimes,
and non-obvious workarounds beside the invariant they concern. Avoid a comment
that only restates the following instruction.

Comments state current assumptions and obligations. Apply
[direct-statements](../../direct-statements/SKILL.md) to comments and examples.

## Exceptions and review

Preserve system-value semantics, compiler directives, register syntax,
generated regions, and external interface names. Make an exception clear at
its owning boundary and in the relevant project requirement or review
explanation. Put recurring exceptions in explicit project requirements.

Examine all applicable naming families, stage fields, conversions, precision
requirements, include structure, layout forms, directives, bindings, and
comments. Use semantic inspection to assess the behavior that compilation and
formatting alone cannot establish.
