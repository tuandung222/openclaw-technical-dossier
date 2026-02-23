# 23 - AI Agent Engineer Playbook

## Nhiệm Vụ Điển Hình

- thêm tool mới
- thêm channel action
- chỉnh prompt/policy pipeline
- debug execution/failover

## Workflow Khuyến Nghị

1. Xác định layer cần sửa (agent/tool/channel/plugin).
2. Cập nhật config schema nếu cần capability mới.
3. Viết unit test trước cho policy-sensitive behavior.
4. Thêm e2e test cho route + delivery + permissions.
5. Chạy lint/build/test matrix tối thiểu.

## Điểm Nóng Cần Hiểu Kỹ

- `runEmbeddedPiAgent()`
- `createOpenClawCodingTools()`
- `applyToolPolicyPipeline()`
- `resolveAgentRoute()`
- `resolveSendPolicy()`

## Debug Checklist

- Lỗi không gọi được tool: kiểm tra policy pipeline + schema normalization.
- Lỗi trả lời sai session/channel: kiểm tra route binding + session key derivation.
- Lỗi timeout/queue: kiểm tra lane concurrency + wait diagnostics.

## Định Hướng Refactor An Toàn

- giữ granularity module nhỏ
- thay đổi behavior kèm regression test ID-driven
- tránh bypass policy ở layer business logic
