# 09 - Sandbox And Exec Approvals (Deep)

## Sandbox subsystem map

`src/agents/sandbox/*` bao phủ:

- config resolution
- workspace mount model
- docker args construction
- runtime status explanation
- tool policy bridging

## Sandbox policy behavior

`pickSandboxToolPolicy()` hỗ trợ `allow`/`alsoAllow`/`deny`.

Semantics quan trọng:

- `alsoAllow` hoạt động additive
- nếu chỉ có `alsoAllow`, hệ thống tự tạo implicit allow baseline để tránh misconfig “không chạy gì”

## Exec approvals lifecycle

`createExecApprovalForwarder()` xử lý nhịp approval notification:

1. nhận approval request
2. lọc theo config/agent/session
3. resolve targets (session target + explicit target)
4. gửi thông điệp approval / resolved / expired

## Approval decision model

Các quyết định chính:

- `allow-once`
- `allow-always`
- `deny`

Với timeout, approval trở thành expired để fail-safe.

## Boundary between sandbox and approvals

- Sandbox hạn chế phạm vi khả năng chạy.
- Approval kiểm soát từng command nhạy cảm bên trong phạm vi còn lại.

## Practical hardening

- Chỉ forward approvals tới kênh đã qua pairing/allowlist.
- Gắn log correlation id giữa approval id và run id.
- Tách metrics approval latency để tối ưu UX mà không hạ security.
