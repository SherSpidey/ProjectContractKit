---
name: hlsl-style
description: Apply HLSL conventions to shader entry points, shared includes, helpers, and stage interfaces.
---

# HLSL Style

Read the [complete writing rules](references/style-rules.md) and apply the
package's authority order and project exceptions. Inspect the target stage,
declarations, includes, and output consumers; preserve numeric semantics,
bindings, and stage ABI while changing only the intended code.

Review names, data, numeric meaning, dependencies, layout, directives, interfaces,
and comments. Respect system semantics, registers, compiler requirements,
generated regions, and external interfaces. Keep exceptions explicit; recurring
project choices belong in the project contract when maintenance is authorized.
