# 23 - AI Agent Engineer Playbook (Deep)

## Core loop cho một thay đổi an toàn

1. Xác định module chủ đích (`agents`, `gateway`, `plugins`, `channels`, `memory`).
2. Viết failing test cho behavior cần đạt.
3. Sửa implementation với thay đổi tối thiểu theo seam.
4. Chạy test matrix liên quan + lint/build.
5. Thêm logging/diagnostic nếu thay đổi runtime-critical.

## Debug playbook

### Agent trả lời chậm

- kiểm tra lane queue depth
- kiểm tra provider latency/fallback chain
- kiểm tra tool-call loops

### Agent không gọi tool

- kiểm tra policy pipeline từng step
- kiểm tra schema compatibility patch
- kiểm tra tool registration/plugin load state

### Trả lời sai session/channel

- kiểm tra route match `matchedBy`
- kiểm tra session key derivation
- kiểm tra send policy override

## Implementation guardrails

- không bypass policy filters “tạm thời”
- không gộp refactor lớn với behavior change lớn
- luôn thêm negative tests cho safety-critical paths
