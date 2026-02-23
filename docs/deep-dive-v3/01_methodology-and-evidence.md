# 01 - Methodology And Evidence

## Epistemic stance

Tài liệu này áp dụng nguyên tắc:

- implementation-over-marketing
- falsifiability-over-narrative
- compositional reasoning-over ad-hoc interpretation

## Evidence classes

### E1 - Static source evidence

Đọc trực tiếp các module orchestration và core execution paths.

### E2 - Structural metrics

Thống kê kích thước, module density, test density để suy ra complexity pressure.

### E3 - Runtime interface evidence

Phân tích contracts ở gateway methods, plugin contracts, policy APIs.

## Snapshot metrics used

- total files: ~6,245
- `src` LOC: ~654,679
- TS files: ~4,427
- test/e2e/live files in `src`: ~1,355
- plugin manifests: 36

## Limits

- Không chạy benchmark latency/throughput thực nghiệm trong lượt này.
- Không reverse-engineer toàn bộ native app internals.
- Không claim correctness proof; chỉ nêu proof obligations và verification roadmap.

## Reproducibility protocol

Muốn tái lập phân tích:

1. checkout commit `445c7a65e...`
2. chạy cùng tập lệnh thống kê file/module
3. trace lại call chains trong modules được chỉ định
4. so sánh output với invariant statements trong các chương
