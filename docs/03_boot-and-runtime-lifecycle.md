# 03 - Boot And Runtime Lifecycle

## Entry Chain

Luồng khởi động CLI đi theo chuỗi:

1. `src/entry.ts`
2. `src/index.ts`
3. `src/cli/program.ts` (qua `buildProgram()`)
4. command handler cụ thể (`gateway`, `agent`, `send`, ...)

## Điểm Quan Trọng Trong `entry.ts`

- Chuẩn hóa env ngay từ đầu (`normalizeEnv`).
- Cấu hình màu terminal (`--no-color`).
- Cơ chế respawn process để suppress `ExperimentalWarning` ổn định.
- Parse profile flag sớm để sync env profile trước khi load CLI commands.

## Runtime Guard

Trong `src/index.ts`:

- `assertSupportedRuntime()` kiểm tra runtime version tương thích.
- `enableConsoleCapture()` chuyển console output vào structured logging.
- Cài global handlers cho `unhandledRejection` và `uncaughtException`.

## Runtime IO Abstraction

`src/runtime.ts` cung cấp `RuntimeEnv`:

- `log`, `error` có behavior khác trong test
- `exit` được bọc để restore terminal state
- `createNonExitingRuntime()` phục vụ unit test

## Tại Sao Thiết Kế Này Quan Trọng

- Giảm entropy từ môi trường (NODE_OPTIONS, argv, profile).
- Tăng tính quan sát lỗi ngay từ boot.
- Giảm side-effect giữa chế độ CLI thực và test runtime.
