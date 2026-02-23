# 26 - Risks Tech Debt And Roadmap

## Risk Register

### R1: Độ phức tạp policy đa tầng

- Triệu chứng: khó suy luận allow/deny cuối cùng.
- Tác động: bug quyền truy cập khó debug.
- Giảm thiểu: policy explain API + trace logs theo step.

### R2: Coupling giữa gateway runtime và extension behavior

- Triệu chứng: plugin lỗi có thể ảnh hưởng startup path.
- Tác động: degrade availability.
- Giảm thiểu: sandbox/plugin isolation + startup health gates.

### R3: Retrieval quality variance theo provider availability

- Triệu chứng: fallback sang FTS-only làm quality dao động.
- Tác động: memory recall không ổn định.
- Giảm thiểu: monitoring mode switch + offline eval alarms.

### R4: Bề mặt tấn công từ remote control surfaces

- Triệu chứng: config lệch auth/scope.
- Tác động: privilege misuse.
- Giảm thiểu: mandatory audit and policy baseline profiles.

## Technical Debt Ưu Tiên

1. Policy explainability end-to-end.
2. Unified observability schema cho gateway/agent/tool/memory.
3. Stronger contract tests cho plugin compatibility.
4. Benchmark suite chính thức cho retrieval + fallback quality.

## Roadmap 3 Pha

### Pha 1 (4-6 tuần)

- implement policy decision trace
- add safety regression tests for tool routing
- publish baseline dashboards

### Pha 2 (6-10 tuần)

- plugin failure isolation improvements
- retrieval eval pipeline CI/nightly
- auth-profile health scoring

### Pha 3 (10-16 tuần)

- adaptive policy recommendation engine
- automatic fallback tuning by telemetry
- architecture hardening cho multi-tenant scenarios

## Closing

OpenClaw hiện đã có nền tảng rất mạnh cho personal agent platform. Bước tiếp theo để lên enterprise-grade là tăng khả năng giải thích quyết định runtime, chuẩn hóa observability và tự động hóa quality loops.
