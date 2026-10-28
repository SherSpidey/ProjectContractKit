---
name: consistency-first
description: Resolve open implementation choices from applicable project code and history, and obtain decisions for significant changes to responsibilities, interfaces, ownership, or dependencies.
---

# Consistency First

Start with the project's agreed requirements. For a choice they leave open,
identify the responsibility, owner, data flow, lifetime, affected API, and
failure boundary. Search local code and relevant history for the same role.

Inspect the closest implementation together with its callers. Start with the
same symbol or overload family and module, then examine the relevant lifecycle
stage, language construct, framework API, and neighboring roles. Broaden the
search when those examples do not establish a suitable form.

Compare examples that have different ownership or failure behavior. History
can explain which patterns are active and repeatedly used. An isolated example
or an example whose lifetime does not fit is insufficient justification.
An agreed project requirement takes priority over incompatible existing code.

Use a suitable precedent's naming, layout, lifecycle, ownership, and failure
behavior. When explaining a choice, identify the concrete files or symbols
that support it.

When the available patterns conflict or no suitable precedent exists:

- Follow any design decision already supplied by the user within its scope.
- Obtain the user's decision before introducing an unresolved significant
  change to module responsibilities, public interfaces, ownership paths,
  lifetime or threading guarantees, or dependency direction.
- Choose an ordinary local implementation directly when it stays within the
  agreed responsibilities, interfaces, ownership, and failure behavior.

Explain the missing decision and its concrete effect when clarification is
needed. Continue independent work that does not depend on it. A decision
already authorized by the user does not need repeated approval.

Avoid redundant registration routes, duplicate lookup ownership, helpers that
conceal ownership, and wrappers whose sole role is forwarding an API. A bridge
needs an actual caller, a real boundary, one owner, and explicit lifetime and
failure behavior. ABI, thread, resource, lifetime, and error boundaries can
justify such a bridge. Assess it with the project's applicable validation.

Add compatibility behavior only for a current caller or an explicit requirement.
Reuse must fit the actual responsibility. Keep lasting project decisions in the
contract when contract maintenance is authorized.
