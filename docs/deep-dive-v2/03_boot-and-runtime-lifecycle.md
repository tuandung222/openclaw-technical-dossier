# 03 - Boot And Runtime Lifecycle (Deep)

## Stage 0 - Process envelope

`src/entry.ts` xử lý các nhiệm vụ “khó rollback” ngay từ đầu:

- normalize env
- suppress warning strategy bằng respawn guard
- CLI profile extraction trước khi nạp command graph

Điểm đáng chú ý: `OPENCLAW_NODE_OPTIONS_READY` tránh respawn vòng lặp.

## Stage 1 - Runtime invariants

`src/index.ts` cài:

- runtime version guard
- console capture (cho structured logging)
- unhandled rejection / uncaught exception handlers

Điều này giảm trạng thái “silent fail” ở production.

## Stage 2 - Command dispatch

`buildProgram()` (CLI layer) là dispatch root cho:

- gateway mode
- agent run mode
- chat/send/monitor/admin commands

## Stage 3 - Long-running services

Khi vào gateway runtime:

- config snapshot + migration + validation
- plugin bootstrap
- channel monitor attachment
- ws/http serving

## Exit path

`defaultRuntime.exit` restore terminal state trước khi `process.exit`, giúp tránh terminal corruption khi crash/abort.

## Failure considerations

- respawn logic lỗi -> CLI có thể dead-start
- runtime guard mismatch -> fail-fast (đúng chủ đích)
- uncaught branch -> vẫn log được trace trước exit

## Engineering takeaway

Boot path được thiết kế fail-fast + observability-first, phù hợp hệ thống có nhiều external integration.
