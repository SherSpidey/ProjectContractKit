# Unity Shader Writing Rules

Use Unity's [ShaderLab manual](https://docs.unity3d.com/2022.3/Documentation/Manual/shader-shaderlab-code-blocks.html)
and [URP shader example](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@14.0/manual/writing-shaders-urp-basic-unlit-structure.html)
as the baseline. Consult documentation and shader libraries for the installed
Unity and pipeline versions; these links do not select a project version.

Unity's [Graphics formatting configuration](https://github.com/Unity-Technologies/Graphics/blob/master/.editorconfig)
uses four-space indentation for shader sources. Brace layout and shader forms
below follow the manual examples; examples do not establish universal rules
for every pipeline. Apply project choices and external interface requirements.

## Layout and file roles

Use four spaces. Put opening braces on separate lines for multiline ShaderLab
blocks and HLSL functions, structs, and control flow. Allow compact ShaderLab
blocks shown in Unity's templates. Keep HLSL declarations and preprocessor
directives on separate lines. Separate meaningful ShaderLab sections and HLSL
operations.

Use `.shader` for ShaderLab, `.hlsl` for Unity shader includes, and `.compute`
for compute stages. Keep ShaderLab structure in its shader file. Use
`HLSLPROGRAM`/`ENDHLSL` and `HLSLINCLUDE` where supported by the target;
preserve required legacy program blocks when the pipeline needs them.

## Names and numeric spelling

Follow the consuming Unity pipeline's naming families: material properties
such as `_BaseMap`, samplers such as `sampler_BaseMap`, `PascalCase` structs,
and `camelCase` local variables, parameters, and stage fields. Keep meaningful
space suffixes such as `OS`, `WS`, and `CS` on transformed quantities.
Preserve pipeline-specific stage input/output names, function forms, and
entry points named by pragmas.

Keep Unity's supported `float`/`half` precision choices, explicit conversions,
and literal spelling. Do not add suffixes solely to satisfy non-Unity HLSL
defaults. Check the target's [numeric precision rules](https://docs.unity3d.com/2022.3/Documentation/Manual/SL-DataTypesAndPrecision.html).

These are scoped exceptions to the built-in HLSL naming, file-role, and
literal-suffix defaults, including HLSL embedded in ShaderLab and associated
Unity includes or compute files.

## Shader and material interfaces

Keep keyword, property, texture/sampler, semantic, macro, tag, and pass names
consistent with material assets, C# property access, and consuming passes.
Choose tags, includes, variants, and render state for the actual pipeline.

For [SRP Batcher compatibility](https://docs.unity3d.com/2022.3/Documentation/Manual/SRPBatcher.html),
keep material constants in the required `UnityPerMaterial` constant buffer.
Do not impose an SRP-only layout on a Built-in Render Pipeline shader.
Validate affected material bindings, variants, and rendering through the
project's actual validation path.
