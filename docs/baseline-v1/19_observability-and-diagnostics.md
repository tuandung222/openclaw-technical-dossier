# 19 - Observability And Diagnostics

## Logging Subsystem

`src/logging/subsystem.ts` cung cấp logger theo subsystem:

- level-aware (trace/debug/info/warn/error/fatal)
- console + file split
- pretty/compact/json style
- subsystem filtering

## Mục Tiêu Thiết Kế

- Người vận hành đọc được ngay luồng theo subsystem (`gateway`, `discord`, `memory`, ...).
- Tránh phá hỏng terminal UX (clear progress line trước khi log).
- Giữ structured logs cho postmortem.

## Queue Diagnostics

`src/process/command-queue.ts` có lane diagnostics:

- enqueue/dequeue logging
- wait-time warnings
- active task tracking
- lane reset mechanism cho restart scenarios

## Security Diagnostics

`src/security/audit.ts` cung cấp security audit report với severity (`info/warn/critical`) và summary counts.

## Production Checklist

- Bật đủ file logging cho forensic.
- Thu lane wait metrics cho command starvation detection.
- Chạy security audit định kỳ sau mỗi thay đổi config lớn.
