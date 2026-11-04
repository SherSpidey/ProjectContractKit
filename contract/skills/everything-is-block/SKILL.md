---
name: everything-is-block
description: Make responsibility, data flow, ownership, and lifetime visible at module, type, function, and local-operation boundaries.
---

# Everything Is a Block

Give each module, file, type, function, and local operation a coherent
responsibility. Establish its owner, inputs, outputs, lifetime, and failure
boundary. Keep state and operations with the owner of their invariants.

Keep one operation together; use blank lines where responsibility, data stage,
ownership, or control-flow meaning changes. Judge local work by its immediate
effects: preparing input, validating distinct facts, creating, configuring,
consuming resolved input, publishing, and recording completion can be separate
stages even within one function's purpose.

Keep an operation with its own guard. A short calculation chain or related
component update can form one result; closely related calls may share a success
condition and failure handling. Names, types, calls, or a return alone do not
require a split. Preserve coherent grouping; a shared final purpose or dependency
does not erase a real handoff.

Read the complete unit, including branches and loops. Identify successive
operations, then inspect original lines at their handoffs for actual whitespace.
A brace is not a blank line. Explain a missing boundary through the work on each
side. Check callers, ownership, and failure behavior as well as local grouping.

Present the main flow before supporting detail and keep sibling operations at
compatible abstraction levels. Preserve execution order, lifetime, and error
propagation when regrouping. Extract helpers for concrete responsibilities,
useful reuse, test seams, or lifecycle boundaries; line counts, decoration, or
forwarding alone do not justify another layer.
