# Unity Constraints

These minimal defaults follow Unity's manuals and API documentation. Apply
them within the installed Unity version and the project's actual configuration.

## Lifecycle and objects

Use the documented [callback order](https://docs.unity3d.com/2022.3/Documentation/Manual/ExecutionOrder.html);
do not depend on an unspecified order between GameObjects. Match initialization,
subscriptions, and cleanup to the owning object's active or instance lifetime.
Call main-thread-only Unity APIs on the main thread, including from asynchronous
work or serialization callbacks; check each API's documented thread support.

Check [Unity object validity](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Object.html)
with Unity's equality or Boolean semantics when native-object lifetime matters.
`?.`, `??`, and managed-reference null tests do not establish that validity.
Use `Destroy` during play; reserve `DestroyImmediate` for appropriate Editor
operations. Release owned native resources and detach subscriptions when their
owner's relevant lifetime ends.

## Serialized data and asset identity

Follow Unity's [serialization rules](https://docs.unity3d.com/2022.3/Documentation/Manual/script-Serialization.html)
for supported fields and types; use `[SerializeField]` for private serialized
fields. Preserve existing serialized data when changing names or types.
Use [FormerlySerializedAs](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Serialization.FormerlySerializedAsAttribute.html)
for supported field renames; type or script migrations need their own handling.

Preserve [asset metadata](https://docs.unity3d.com/2022.3/Documentation/Manual/AssetMetadata.html)
and GUIDs. Move or rename assets with their `.meta` files, and verify affected
scene, Prefab, material, and ScriptableObject references.

## Editor changes

Keep UnityEditor dependencies in Editor-only assemblies or correctly guarded
code. For custom Inspector field edits, prefer
[SerializedObject/SerializedProperty](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/SerializedObject.html)
with synchronized reads and `ApplyModifiedProperties`.
For direct user-facing edits, use the appropriate Undo API before mutation;
record Prefab-instance overrides where required, and save the intended assets.
Follow [Undo.RecordObject](https://docs.unity3d.com/2022.3/Documentation/ScriptReference/Undo.RecordObject.html)
and the dedicated APIs for creation, destruction, or reparenting.

## Enter Play Mode

Check the actual Domain Reload and Scene Reload settings. When
[Domain Reload is disabled](https://docs.unity3d.com/2022.3/Documentation/Manual/DomainReloading.html),
reset static state and event registrations that should not survive a play
session. Verify repeated entry and exit using that configuration; do not
change project-wide reload settings as a substitute for correct lifecycle work.

Use the project's affected Editor and Player validation paths. Its architecture,
asset generation, networking, and acceptance rules remain project requirements.
