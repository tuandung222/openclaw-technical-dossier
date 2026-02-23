# 01 - Analysis Method And Snapshot (Deep)

## Nguồn dữ liệu

Phân tích dựa trên:

- static code reading ở các module orchestrator
- call-chain tracing qua import graph
- thống kê repository bằng `rg/find/wc`
- kiểm tra metadata Git để cố định mốc thời gian

Không sử dụng suy đoán theo docs marketing; ưu tiên implementation behavior.

## Snapshot kỹ thuật

- Total files: ~6,245
- LOC trong `src/`: ~654,679
- TS files toàn repo: ~4,427
- markdown docs trong `docs/`: ~641
- tests trong `src` (pattern test/e2e/live): ~1,355
- plugin manifests: 36

## Phương pháp tách lớp tài liệu

### Lớp 1 - Runtime Structure

Mô tả entrypoints, composition roots, request handling và state boundaries.

### Lớp 2 - Execution Mechanics

Đi sâu pipeline agent/model/tool/memory/queue với focus vào invariants và fallback.

### Lớp 3 - Governance & Ops

AuthZ, security audit, deployment model, observability, QA.

### Lớp 4 - Persona Actionability

Playbook chuyển hóa tri thức code thành quyết định kỹ thuật thực dụng.

## Tiêu chí “deep-dive” trong bộ V2

- nêu rõ module cụ thể và trách nhiệm
- chỉ ra thứ tự xử lý trong runtime path
- chỉ ra trade-off và failure mode chính
- có hướng refactor/test tương ứng

## Các điểm đã được cập nhật so với baseline v1

- snapshot mới sau pull ngày 2026-02-24 (giờ local)
- quy mô code tăng mạnh ở `agents`, `gateway`, `infra`, `channels`
- mật độ test tăng rõ rệt
- nhiều module mới liên quan security/tool policies và runtime hardening
