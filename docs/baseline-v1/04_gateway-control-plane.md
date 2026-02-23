# 04 - Gateway Control Plane

## Vai Trò

Gateway là control plane trung tâm cho:

- WS protocol + HTTP endpoints
- channel adapters
- cron + heartbeat
- node/device integration
- auth/rate-limit
- plugin/runtime composition

## Điểm Vào Chính

- `src/gateway/server.impl.ts`
- `startGatewayServer(port, opts)`

## Startup Flow (rút gọn)

1. Đọc + migrate config legacy nếu cần.
2. Validate config snapshot.
3. Auto-enable plugin theo policy/config.
4. Khởi tạo diagnostic heartbeat (nếu bật).
5. Init subagent registry.
6. Load plugin registry + channel methods.
7. Setup channel manager / node registry / exec approvals.
8. Gắn WS handlers + HTTP handlers.
9. Bật discovery, tailscale exposure, maintenance timers.

## Thành Phần Trọng Yếu

- `NodeRegistry`: quản lý node pair/invoke lifecycle
- `ExecApprovalManager`: approval state cho exec commands
- `createGatewayRuntimeState`: runtime state trung tâm
- `loadGatewayPlugins`: nạp plugin handlers + channel plugins
- `attachGatewayWsHandlers`: wire protocol layer vào runtime

## Tín Hiệu Kiến Trúc

- Gateway thiết kế theo kiểu composition root: gom dependency và orchestration tại một điểm.
- Mức tách module cao: auth, health, cron, channels, reload đều có file riêng.
- Ưu tiên graceful operations: reload hooks, restart deferral, queue checks.
