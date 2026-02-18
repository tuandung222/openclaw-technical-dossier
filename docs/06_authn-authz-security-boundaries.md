# 06 - AuthN AuthZ Security Boundaries

## Security Boundary Lớn

OpenClaw chạm trực tiếp vào messaging channels và command execution, nên boundary quan trọng nằm ở:

- Gateway auth
- Method scopes
- Tool policy
- Sandbox policy
- Channel pairing/allowlist

## Gateway-Level Security

Từ `src/security/audit.ts` và gateway auth modules:

- Phân biệt `token` vs `password` mode
- Kiểm tra kết hợp bind mode + tailscale mode + auth mode
- Cảnh báo cấu hình mở (funnel/public + weak auth)
- Kiểm tra permissions của state dir và config file

## Method Authorization

`src/gateway/server-methods.ts`:

- `node` role chỉ được gọi một tập method giới hạn (`node.event`, `node.invoke.result`, ...)
- Operator không có scope phù hợp sẽ bị chặn theo method class
- Admin-level methods bị khóa cứng

## Channel Security

`security audit` gọi `collectChannelSecurityFindings` để audit:

- DM policy
- allowlist
- pairing behavior
- exposure drift

## Practical Takeaways

- Không xem gateway auth là đủ, vì tool execution còn phụ thuộc policy pipeline.
- Security stance là multi-layer, không phải single control.
- Audit subsystem dùng được như preflight check trước production rollout.
