---
name: consistency-first
description: Ground requirement application and open choices in suitable project precedents, and obtain missing significant design decisions.
---

# Consistency First

## Find project evidence

Before implementing or reviewing, identify applicable requirements and establish
the affected responsibility, ownership, data flow, lifetime, API, and failure
behavior. Search local code and history for the same responsibility. Start with
the nearest symbol family and callers, then broaden to related roles and
mechanisms as needed.

Use precedents that meet current requirements and fit those boundaries to
interpret requirements and resolve open choices. Proximity or repetition alone
does not establish suitability. Preserve applicable naming, layout, lifecycle,
and interface forms. Cite concrete files or symbols and explain necessary differences.

Explicit requirements and authorized decisions govern when examples conflict
or are absent. State a missing precedent.

## First-principles analysis

Use this analysis for a new or changed design boundary, a material choice
unresolved by project precedents, or a failure with an unclear cause. Start
with the required observable outcome and the facts that constrain it. Identify
what must hold for the affected inputs, state, ownership, lifetime, and failure
paths. Mark assumptions that could change the decision.

For a design choice, derive a candidate from those constraints. Compare it
with viable alternatives and suitable project precedents. Prefer the simplest
approach that satisfies the constraints and covers the whole responsibility.

For a defect, trace the inputs and state transitions to the observed failure
and seek evidence that distinguishes plausible causes.

## Apply decisions

Apply decisions already authorized. Obtain a decision for unresolved significant
changes to responsibilities, public interfaces, ownership, lifetime, threading,
or dependency direction before making the affected change. Explain the
consequence and continue independent work. Make ordinary local choices within
agreed boundaries.

Avoid redundant registration, lookup ownership, concealed owners, and forwarding
wrappers. A bridge needs a current caller, a real boundary, one owner, and explicit
lifetime and failure behavior, assessed by applicable project validation.
Compatibility serves a current caller or explicit requirement.

Record lasting project decisions in the contract when maintenance is authorized.
