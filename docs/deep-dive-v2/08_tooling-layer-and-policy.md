# 08 - Tooling Layer And Policy (Deep)

## Tool factory responsibilities

`createOpenClawCodingTools()` chịu trách nhiệm:

- assemble tool registry runtime
- inject context (channel/session/agent/workspace)
- apply schema compatibility transforms
- apply policy filters qua pipeline nhiều bước

## Policy pipeline semantics

`buildDefaultToolPolicyPipelineSteps()` tạo chuỗi policy theo precedence thực tế.

Thứ tự quan trọng vì mỗi bước có thể giảm toolset thêm.

## Plugin-aware policy features

- build plugin tool groups
- expand group alias thành tool entries
- strip unknown plugin-only allowlists để tránh accidental deny toàn bộ core tools

## Provider-compatibility behavior

- schema clean cho Gemini
- Claude parameter compatibility patch
- normalization wrappers trước execution

## Guardrails

- workspace root guard
- owner-only tool policy
- subagent depth/tool policy inheritance
- explicit/implicit message target gating

## Deep takeaway

Tool policy ở OpenClaw là một authorization engine thực thụ, không chỉ là danh sách allow/deny tĩnh.
