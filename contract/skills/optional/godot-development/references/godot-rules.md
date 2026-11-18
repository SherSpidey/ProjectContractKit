# Godot Constraints

These minimal defaults follow Godot 4's manuals and API documentation. Apply
them within the project's actual engine version, language binding, and settings.

The project defines architecture, Autoload use, asset generation, networking,
directory layout, and acceptance criteria.

## Initialization and node lifetime

Follow the documented [Node callbacks](https://docs.godotengine.org/en/stable/classes/class_node.html):
`_enter_tree()` runs parent before children; `_ready()` runs children before
parent. `_ready()` normally runs once per node. Re-entry initialization must
account for this; `request_ready()` schedules another call on the next entry
for the requesting node, not its children.

Read [saved exported values](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_exports.html)
after deserialization when those values are required. In GDScript, `_init()`
sees defaults before saved scene/resource values are assigned. Initialize child
node dependencies at an appropriate ready phase. Keep `@onready` separate from
`@export` on the same variable; its later initialization can overwrite the
exported value, as described in the
[GDScript reference](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_basics.html#onready-annotation).

Distinguish manually managed `Object`/`Node` instances from `RefCounted`/`Resource`,
using the binding's reference-counting and disposal behavior. Deleting a node
also deletes its children. `remove_child()` detaches without deleting; keep
responsibility for cleaning up detached subtrees explicit. Use `queue_free()`
for ordinary deferred node deletion and account for the delay before destruction.

Across callbacks, deferred work, or `await`, recheck references when the
operation can outlive its targets. Use the binding's
[object-validity check](https://docs.godotengine.org/en/stable/classes/class_object.html#class-object-method-free)
(`is_instance_valid()` in GDScript); a non-null reference can already be invalid.
Check queued deletion too when the operation requires a target that will remain
active. Keep subscriptions and work within their intended active or instance
lifetime.

## Resources and serialized identity

Loaded [resources](https://docs.godotengine.org/en/stable/classes/class_resource.html)
can share a cached instance. Choose intentional shared mutation or isolated
instance data before changing one. Where isolation is required, use the target
version's appropriate duplication or `resource_local_to_scene` behavior and
inspect nested resources. Changing `resource_local_to_scene` at runtime does
not retroactively isolate existing scene instances.

Preserve stored property names and values in scenes and resources. Treat export
renames and type changes as data migrations; verify affected `.tscn`/`.tres`
data, node paths, and signal bindings. Preserve resource UIDs and check both UID
and path-based references when moving or renaming assets. In versions using
[companion `.uid` files](https://godotengine.org/article/uid-changes-coming-to-godot-4-4/),
keep those files in version control and move them with their source files.

## Signals and threads

Follow the binding's [signal connection behavior](https://docs.godotengine.org/en/stable/classes/class_object.html#class-object-method-connect)
and flags. Avoid unintended duplicate connections; end subscriptions when
their intended lifetime ends. Automatic disconnection depends on the emitter,
receiver, and callable. For
[C# signals](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_signals.html#disconnecting-automatically-when-the-receiver-is-freed),
capturing lambdas and custom signals can require explicit disconnection when
the receiver is freed first; retain the delegate needed to unsubscribe.

Respect [thread-safe API boundaries](https://docs.godotengine.org/en/stable/tutorials/performance/thread_safe_apis.html).
Arbitrary worker-thread access to the active scene tree is unsafe. Use documented
handoffs such as deferred calls where appropriate, and synchronize shared data.
Check the API and relevant thread settings; prevent concurrent mutation of
shared resources.

## Editor changes and scene persistence

Distinguish runtime parenting and destruction from `Node.owner`, which governs
scene persistence. When set, the owner must be an ancestor of the node. For nodes
intended to be saved with a scene, establish the correct owner after parenting;
`add_child()` alone does not make an Editor-added node persist when saving the
scene.

Keep [tool-script execution](https://docs.godotengine.org/en/stable/tutorials/plugins/running_code_in_the_editor.html)
appropriate to the Editor or runtime context, using `Engine.is_editor_hint()`
or its binding equivalent where needed. Scope mutations to the intended scene
or resource.

For Editor edits that integrate with undo history, use
[EditorUndoRedoManager](https://docs.godotengine.org/en/stable/classes/class_editorundoredomanager.html)
with the correct context and do/undo operations.

When a tool or Editor script mutates a scene that must be saved, explicitly
establish the dirty state the Editor uses to recognize unsaved scene changes.

## Validation

Use the project's affected script, scene, Editor, and export checks. Follow
[validation and acceptance](../../../core/pck-workflow/SKILL.md#validation-and-acceptance)
for check ownership.

When using the Godot CLI, check the installed tool's supported
[command-line options](https://docs.godotengine.org/en/stable/tutorials/editor/command_line_tutorial.html).
`--check-only` with `--script` supplies script parsing evidence.

Use separate checks for affected scene bindings, lifecycle behavior, gameplay,
and rendering.

When a tool or Editor script makes scene mutations that must persist, verify
the intended changes after saving and reopening the affected scene.
