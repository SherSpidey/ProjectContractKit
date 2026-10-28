---
name: everything-is-block
description: Keep responsibility, data flow, ownership, and lifetime clear when designing, editing, or reviewing code at module, type, function, and local-flow boundaries.
---

# Everything Is a Block

Treat each module, file, type, function, and local operation as a unit with a
coherent responsibility. Understand its owner, inputs, outputs, lifetime, and
failure boundary before choosing its shape.

Keep the statements that perform one operation together. Introduce a boundary
where responsibility, data stage, ownership, or control-flow meaning changes.
Use whitespace to expose that boundary. A small operation can be one compact
block; examine a longer operation through its actual work and ownership stages.

Present the main flow before its supporting detail. Keep sibling operations
at compatible abstraction levels. Preserve required execution order, resource
lifetime, and error propagation when grouping or extracting work.

Create a helper for a concrete responsibility, useful reuse, a test seam, or a
lifecycle boundary. Keep the caller's data flow and ownership understandable.
Line counts, decorative sections, and a forwarding layer alone do not justify
an extraction.

Keep state and operations with the owner responsible for their invariants.
For work that resolves input, prepares a value, and publishes a resource, expose
separate stages when their data or ownership duties differ. Keep the tightly
related statements inside each stage together.

When reviewing a change, examine the responsibilities and handoffs in the
actual code. Check whether each boundary explains an operation and whether the
caller can still see who owns the state. Use relevant files or symbols when
explaining a judgment. Formatting and successful parsing establish only the
mechanical properties they inspect; cohesion and ownership require reading
the implementation.
