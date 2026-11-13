---
name: consistency-first
description: Ground requirement application and open choices in suitable project precedents, and obtain missing significant design decisions.
---

# Consistency First

Before implementing or reviewing, identify the applicable requirements and search
local code and history for how the same responsibility is expressed. Establish
ownership, data flow, lifetime, API, and failure behavior; inspect the nearest
symbol family and its callers, broadening to related roles and mechanisms as needed.

Check precedents against current requirements and their fit to the responsibility,
ownership, lifetime, and failure behavior. Proximity or repetition alone does not
establish suitability. Use conforming examples to interpret requirements and
resolve open choices; preserve their applicable naming, layout, lifecycle, and
interface form. Cite concrete files or symbols and explain necessary differences.

Requirements remain authoritative when examples conflict or are absent. State a
missing precedent and follow explicit requirements and authorized decisions;
obtain any unresolved significant decision before introducing a new pattern.

Apply decisions already authorized. Ask only for unresolved significant changes
to responsibilities, public interfaces, ownership, lifetime, threading, or
dependency direction; explain the consequence and continue independent work.
Ordinary local choices within agreed boundaries need no repeated approval.

Avoid redundant registration, lookup ownership, concealed owners, and forwarding
wrappers. A bridge needs a current caller, a real boundary, one owner, and explicit
lifetime and failure behavior, assessed by applicable project validation.
Compatibility serves a current caller or explicit requirement. Record lasting
project decisions in the contract when maintenance is authorized.
