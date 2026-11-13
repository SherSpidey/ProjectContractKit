---
name: renderdoc-cmd
description: Use RenderDoc from a terminal to capture frames, inspect events, pipeline state and shader inputs, and export rendered images without GUI interaction.
---

# RenderDoc from the Terminal

## Choose the tools

- Reuse an existing `.rdc` when it covers the question.
- Find installed RenderDoc tools and read the relevant command's `--help`.
  Upstream RenderDoc, forks, and wrappers have different command sets.
- Use an available MCP/CLI wrapper or the official Python Replay API for headless
  inspection. Native `renderdoccmd replay` opens a window. Python bindings must
  match the library version, architecture, and interpreter ABI.

## Capture

- Launch with `renderdoccmd capture`, setting `--working-dir`, `--capture-file`,
  and application arguments. Request capture through the application API or
  target control; `--wait-for-exit` only waits for termination.
- For direct instrumentation, load RenderDoc before graphics initialization and
  obtain `RENDERDOC_GetAPI` with a matching header and supported version. After
  warm-up, bracket rendering with `StartFrameCapture` / `EndFrameCapture`.
  This supports offscreen work without presentation. Keep the library loaded;
  avoid overlapping captures and ambiguous null device/window handles.
- Retrieve the completed capture's actual filename through `GetCapture` or
  target-control messages. If capture stalls, inspect logs to distinguish
  injection, initialization, and trigger failures.

## Inspect efficiently

For standalone Python, use `renderdoc`; `pyrenderdoc` belongs to the GUI.
Call `InitialiseReplay` once, open the capture, and reuse one replay controller.
Keep replay calls on one thread. Release controllers and capture handles before
`ShutdownReplay`; close wrapper sessions when finished.

Start with `GetRootActions()` and recursively visit `children`. Narrow to the
relevant pass, draw, or dispatch; filter detailed queries by event, resource,
or shader stage. Use `SetFrameEvent(eventId, False)` to select the post-event
state; force refresh only when needed. Prefer `GetPipelineState()` for shared
pipeline queries.

| Question | Operation |
| --- | --- |
| What does this event use? | Inspect bound shaders, inputs, descriptors, constants, and outputs. |
| Who writes or reads this resource? | Follow `GetUsage(resourceId)`. |
| What data reached the shader? | Read bound ranges with `GetBufferData`; use `GetCBufferVariableContents` for reflected constants. |
| Why is this pixel wrong? | Use pixel history, then shader debugging if supported. |

Follow actual event bindings, including inherited state, offsets, and subranges.
For missing geometry, inspect draw counts, inputs, transforms, viewport/scissor,
culling, and depth before tracing shader execution.

Export PNG with `TextureSave` / `SaveTexture`, then view it. Choose the actual
output resource, event after the relevant work, mip, slice, and sample. Preserve
alpha and set the HDR display range as needed. The largest texture need not be
the final output; `renderdoccmd thumb` only exports a thumbnail.

Without replay, use supported `renderdoccmd convert` exports for recorded data.
For `zip.xml`, keep XML and ZIP together; resolve payload references and lengths
from metadata. Structured export cannot supply replay-derived images or state.

## References

- [Standalone Python API](https://github.com/baldurk/renderdoc/blob/v1.x/docs/python_api/python_module.rst)
- [Official API examples](https://github.com/baldurk/renderdoc/tree/v1.x/docs/python_api/examples)
- [rdc-cli workflows](https://github.com/BANANASJIM/rdc-cli)
- [Community RenderDoc skill](https://github.com/rudybear/renderdoc-skill)
