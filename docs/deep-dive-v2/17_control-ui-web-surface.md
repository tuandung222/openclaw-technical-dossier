# 17 - Control UI Web Surface (Deep)

## Serving model

Control UI được serve trực tiếp bởi gateway (`control-ui.ts`), không tách riêng backend.

## Security headers and CSP

`applyControlUiSecurityHeaders()` set:

- `X-Frame-Options: DENY`
- CSP
- `X-Content-Type-Options: nosniff`
- `Referrer-Policy: no-referrer`

## Bootstrap contract

UI lấy bootstrap config qua endpoint dedicated để nhận:

- basePath
- assistant name/avatar
- assistant agent id

## Routing and path safety

- normalize base path
- block unsafe relative paths
- explicit 404 behavior cho invalid requests

## Frontend architecture notes

Trong `ui/src/ui` đã tách controller/view/render/tool-stream logic khá rõ, giúp maintainability tốt hơn khi tính năng UI tăng.

## Operational insight

Vì UI là control surface quyền cao, mọi hardening của gateway auth/scope/CSP phải được xem như production-critical controls.
