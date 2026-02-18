# 17 - Control UI Web Surface

## UI Stack

`ui/` dùng:

- Vite
- Lit
- TypeScript
- test với Vitest + Playwright

## UI Serve Model

Gateway serve control UI trực tiếp thông qua `src/gateway/control-ui.ts`.

Các điểm đáng chú ý:

- security headers (`CSP`, `X-Frame-Options`, `nosniff`)
- bootstrap config endpoint cho UI init
- assistant identity/avatar resolution
- static file serving với path safety checks

## Frontend Organization

`ui/src/ui/` chia theo layer:

- controllers
- views
- app lifecycle/render modules
- gateway client helpers
- chat/message render logic

## Tính Chất Kiến Trúc

- Control UI không phải app tách rời backend; nó là extension của gateway control plane.
- Đổi config/session/channel từ UI đi qua cùng gateway method surface như CLI.

## Tác Động Vận Hành

- Cần xem UI như một control surface quyền cao.
- CSP và auth gateway phải luôn được coi là critical controls.
