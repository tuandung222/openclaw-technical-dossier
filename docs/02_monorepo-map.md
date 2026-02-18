# 02 - Monorepo Map

## Tổng Quan

OpenClaw là monorepo TypeScript-first, nhưng chứa thêm Swift/Kotlin/Go/shell để hỗ trợ đa nền tảng và tooling.

## Thống Kê Nhanh

- File toàn repo: ~5,640
- `src/` LOC: ~569k
- `src/` TS files: ~3,174
- Extensions: 36 plugin manifest
- Docs markdown: ~636 file trong `docs/`

## Top Module Theo Số File `src/`

- `agents`: 574
- `commands`: 277
- `gateway`: 238
- `infra`: 237
- `auto-reply`: 218
- `cli`: 214
- `config`: 155
- `browser`: 101
- `channels`: 97
- `memory`: 78

## Cấu Trúc Chính

- `src/`: runtime lõi gateway + agent + channels + memory + security
- `extensions/`: plugin channel/provider/tool mở rộng
- `packages/`: package đóng gói kiểu bot flavor (`clawdbot`, `moltbot`)
- `ui/`: control UI (Vite + Lit)
- `apps/`: mobile/desktop app assets và wrappers
- `docs/`: tài liệu chính thức hệ thống
- `scripts/`: build/test/release/dev tooling

## Monorepo Workspaces

Từ `pnpm-workspace.yaml`:

- root (`.`)
- `ui`
- `packages/*`
- `extensions/*`

## Nhận Định Kiến Trúc

- Core logic tập trung vào `src/gateway` và `src/agents`.
- `extensions/` giúp channel và capability expansion mà không sửa core runtime.
- `config/` và `security/` có bề dày lớn, phản ánh ưu tiên hardening.
- Mật độ test cao cho thấy repo nhấn mạnh regression safety.
