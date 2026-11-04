---
name: consistency-first
description: Resolve open implementation choices from suitable project code and history, and obtain missing significant design decisions.
---

# Consistency First

Follow agreed requirements. For choices they leave open, establish responsibility,
ownership, data flow, lifetime, API, and failure behavior, then search local code
and history for the same role. Inspect the nearest symbol family and its callers;
broaden to related modules, lifecycle stages, and mechanisms as needed.

Use precedents whose ownership and failure behavior fit. Compare conflicting
examples and history rather than treating one occurrence as a convention.
Carry the suitable naming, layout, lifecycle, and interface form into the work;
cite concrete files or symbols when explaining the choice.

Apply decisions already authorized. Ask only for unresolved significant changes
to responsibilities, public interfaces, ownership, lifetime, threading, or
dependency direction; explain the consequence and continue independent work.
Ordinary local choices within agreed boundaries need no repeated approval.

Avoid redundant registration, lookup ownership, concealed owners, and forwarding
wrappers. A bridge needs a current caller, a real boundary, one owner, and explicit
lifetime and failure behavior, assessed by applicable project validation.
Compatibility serves a current caller or explicit requirement. Record lasting
project decisions in the contract when maintenance is authorized.
