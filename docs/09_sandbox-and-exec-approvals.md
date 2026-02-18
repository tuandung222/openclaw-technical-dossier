# 09 - Sandbox And Exec Approvals

## Sandbox Layer

Sandbox API được expose qua `src/agents/sandbox.ts` và các module con:

- `sandbox/config.ts`
- `sandbox/context.ts`
- `sandbox/docker.ts`
- `sandbox/tool-policy.ts`
- `sandbox/runtime-status.ts`

## Sandbox Tool Policy

`pickSandboxToolPolicy()` trong `src/agents/sandbox-tool-policy.ts` có logic đáng chú ý:

- `alsoAllow` được merge additively
- Nếu chỉ có `alsoAllow` mà không có `allow`, hệ thống suy diễn implicit `"*"`
- `deny` vẫn giữ như lớp chặn độc lập

## Exec Approval Architecture

Thành phần:

- `ExecApprovalManager` (gateway)
- `createExecApprovalForwarder` (`src/infra/exec-approval-forwarder.ts`)

Flow tiêu biểu:

1. Request approval được tạo khi exec cần user decision.
2. Forwarder chọn target (session target / config targets / both).
3. Approval status được gửi ra channel (nếu cấu hình bật).
4. Decision (`allow-once`, `allow-always`, `deny`) được apply lại vào runtime.

## Risk Controls

- Filter theo agent/session để tránh spam approval không cần thiết.
- Timeout approval + expiry message.
- Deduplicate targets để tránh duplicate delivery.

## Kết Luận

Sandbox và approvals không tách rời: sandbox giảm capability surface, approvals kiểm soát lệnh nhạy cảm còn lại.
