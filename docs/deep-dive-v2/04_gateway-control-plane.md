# 04 - Gateway Control Plane (Deep)

## Composition root

`startGatewayServer()` trong `src/gateway/server.impl.ts` là nơi lắp ráp toàn bộ subsystem runtime.

## Startup sequence chi tiết

1. Đọc config snapshot.
2. Chạy legacy migration nếu cần.
3. Validate schema và issues.
4. Áp dụng auto-enable plugin.
5. Khởi tạo diagnostics/restart policies.
6. Resolve default agent/workspace.
7. Load plugin registry + channel plugin methods.
8. Tạo channel manager + node registry + exec approvals.
9. Setup health/cache/model catalog/discovery.
10. Attach WS + HTTP handlers.
11. Start sidecars (cron, tailscale exposure, browser control tùy config).

## Runtime state clusters

- config/state snapshots
- connection/client registry
- session/presence versions
- node/device pairing states
- approval queues
- cron/timer states

## Control plane contracts

Gateway phục vụ 2 mặt:

- WS RPC style methods/events
- HTTP compatibility endpoints (`/v1/chat/completions`, responses API, tools invoke)

## Critical reliability controls

- restart deferral dựa trên pending queue + active runs
- health snapshot refresh versioned
- minimal gateway mode cho test

## Deep insight

Gateway không chỉ là API layer mà là orchestrator của một distributed-in-miniature runtime (channels, devices, tools, models, sessions).
