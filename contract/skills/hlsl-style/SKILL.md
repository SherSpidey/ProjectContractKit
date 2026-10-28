---
name: hlsl-style
description: Apply the HLSL writing conventions when editing or reviewing shader entry points, shared includes, helpers, and stage interfaces.
---

# HLSL Style

Read [the complete writing rules](references/style-rules.md) before applying
this Skill. Project requirements determine resource ownership, coordinates,
pipeline interfaces, and local exceptions; this profile supplies language
defaults under the package's priority rules.

Understand the target stage, its declarations and includes, and the consumers
of its outputs. Preserve numeric semantics, resource bindings, and the stage
ABI when editing new or intentionally changed code.

Review the applicable names, data declarations, numeric meaning, dependencies,
layout, directives, interfaces, and comments. Respect system semantics,
registers, compiler requirements, generated regions, and external interfaces.
Keep exceptions explicit at their owning boundary and place recurring project
decisions in the project contract when authorized.
