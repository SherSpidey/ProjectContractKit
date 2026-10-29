# Writing Project Contracts

Use this guide to choose the shape of a project contract and inspect its
finished text. Templates illustrate useful organization. Adapt headings to the
actual content, and omit sections that have nothing to say.

## Content standard

A requirement tells the agent what decision or behavior applies. Make its scope
clear when it is narrower than the containing topic. Keep conditions, limits,
exceptions, and useful examples close to the requirement they qualify.

Preserve the intended obligation strength. A requirement, prohibition,
preference, and permission have different meanings. Use direct wording that
retains those meanings; do not turn a preference into an unconditional command.

A paragraph may contain several obligations. Preserve and review each
obligation and its qualifiers; group related requirements where they can be
understood together.

State the owner, dependency, lifetime, interface, or failure boundary when it
is part of the project's requirement. Include numeric limits and required
validation behavior when the project specifies them. Explain a present
invariant when that explanation is needed to apply the rule correctly.

An exception identifies its applicable condition and the behavior required
there. It does not create a general waiver. A project convention that overrides
a language default identifies the actual choice and its scope.

A topic has a descriptive title and a coherent responsibility. Group related
requirements under headings that express their decisions. Choose titles and
terms that an agent can find from the task's actual concepts. Avoid splitting
a rule away from the condition, exception, or example needed to understand it.

Maintain each requirement in one place. Use ordinary Markdown links to connect
related decisions or identify their authoritative text. Keep the project entry
useful for selecting topics without copying their full requirements.

## Project entry template

Use `contract/project/README.md` for the shared project requirements and topic
navigation. Shared requirements apply across tasks. If a topic document contains
additional requirements that every task needs, identify it explicitly as
required reading.

~~~markdown
# <Project name> contract

<Context needed to understand the shared requirements, when useful.>

## Shared requirements

<Current requirements that apply across the project.>

## Topics

- [<Topic title>](<topic-file>.md): <The responsibilities or decisions it governs.>
~~~

Put a small contract's complete requirements in this entry when they form one
coherent topic. Add topic links as independent topics become useful. Omit an
empty navigation section. Topic filenames describe their subject; they do not
need clause numbers or an enforced naming taxonomy.

## Topic template

Use one file for requirements that are understood and maintained together.
A topic can contain several related requirements.

~~~markdown
# <Topic title>

<Applicable objects, responsibilities, or boundaries, when clarification is needed.>

## <Decision or responsibility>

<Current requirements, with their conditions and exceptions.>

<An explanation or example when it materially clarifies application.>
~~~

Write additional sections only for real parts of the topic. Plain paragraphs
may be sufficient. Lists help separate parallel requirements; tables help
compare cases; code examples clarify exact code shape or interface use.

Examples illustrate the stated scope. Keep the normative requirement explicit
so readers can distinguish a required property from incidental example names
or values. Do not add a requirement solely to complete a template.

## Complete example

The following two files illustrate a project entry and one related topic.
Their renderer decisions belong to this example project.

`contract/project/README.md`:

~~~markdown
# Example renderer contract

## Shared requirements

Scene code uses the renderer's public interface. Scene code must not include
renderer implementation headers.

## Topics

- [GPU resource lifetime](gpu-resource-lifetime.md): ownership of managed textures
  and buffers, borrowed host textures, and safe destruction.
~~~

`contract/project/gpu-resource-lifetime.md`:

~~~markdown
# GPU resource lifetime

These requirements apply to textures and buffers used by the renderer.

## Managed resources

The renderer's resource store owns managed textures and buffers. Scene objects
hold borrowed handles and must not destroy the underlying GPU objects.

Once destruction is scheduled, the resource store rejects new uses of the
handle. It retains the GPU object until submitted commands that use it have
completed.

## Host-owned textures

A texture supplied by the host application remains owned by the host. The
renderer records a borrow and must not destroy the texture.

The renderer releases its borrow after all submitted uses have completed.
The host keeps the texture alive until that borrow has ended.
~~~

The entry expresses a shared dependency rule. The topic keeps resource
ownership, use restrictions, destruction timing, and the host-owned case
together.

## Finished-content requirements

- A reader can identify which topic governs the task and which requirements
  apply within that topic.
- Obligations, preferences, permissions, conditions, limits, and exceptions
  retain the user's intended meaning.
- Each topic is understandable with its clearly identified related requirements;
  examples and necessary explanations remain available beside their rules.
- There is one authoritative statement of each requirement, with compatible
  cross-topic decisions and functioning navigation.
- Reorganization preserves requirements and usable references; additions,
  removals, and changes in obligation are authorized.
- Project exceptions identify the affected default and applicable scope.
- Prose, examples, paths, and referenced interfaces agree with the project's
  actual decisions. Existing capabilities and requirements to implement a
  capability are distinguishable, with a clear owner.
- The maintained text describes current requirements and can be used without
  the input material.
