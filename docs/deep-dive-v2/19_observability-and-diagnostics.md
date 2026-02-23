# 19 - Observability And Diagnostics (Deep)

## Logging architecture

`createSubsystemLogger()` chuẩn hóa logging theo subsystem và target (console/file).

Tính năng quan trọng:

- level gating
- style switching (pretty/compact/json)
- subsystem label normalization
- active progress line safe flush

## Queue diagnostics

`command-queue.ts` emit diagnostics cho:

- enqueue/dequeue
- wait duration vượt ngưỡng
- active task count
- lane reset safety sau restart

## Health and operational traces

Gateway có health versioning + cache refresh flows, giúp client polling và dashboard phản ánh trạng thái ổn định hơn.

## Security observability

`security/audit.ts` trả structured findings với severity và remediation hints, có thể tích hợp thành compliance gates.

## Missing metrics candidates

- fallback chain depth distribution
- tool-policy deny reason frequency
- per-channel inbound parse failure rate
- plugin load/activation latency
