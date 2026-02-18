# 08 - Tooling Layer And Policy

## Tool Factory Chính

`src/agents/pi-tools.ts` tạo `createOpenClawCodingTools(options)`.

Nhóm tool điển hình:

- FS tools (`read`, `write`, `edit`, `apply_patch`)
- Exec/process tools
- Channel action tools
- Gateway/session tools
- Plugin-contributed tools

## Policy Stack

Policy không chỉ một lớp, mà là pipeline nhiều tầng:

- profile policy
- provider profile policy
- global allow policy
- global provider policy
- agent policy
- agent provider policy
- group policy

Triển khai tại:

- `src/agents/tool-policy-pipeline.ts`
- `src/agents/tool-policy.ts`
- `src/agents/pi-tools.policy.ts`

## Kỹ Thuật Đáng Chú Ý

- `stripPluginOnlyAllowlist`: tránh allowlist làm mất tool core do plugin chưa bật.
- expand plugin groups thành tool-level policies.
- schema normalization cho compatibility (Claude/Gemini quirks).
- workspace-root guard cho tool file I/O.

## Tác Động Cho Engineering

- Policy pipeline giúp quản trị privilege rõ theo context.
- Tool surface rất mạnh, nên policy resolution phải được xem như “runtime firewall”.
- Việc thêm tool mới cần kèm rule update + test matrix để tránh privilege escalation.
