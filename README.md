# OpenClaw Technical Dossier

Repository này chứa bộ tài liệu phân tích mã nguồn OpenClaw phục vụ 4 nhóm độc giả:

- Agent Architect
- AI Agent Engineer
- LLM Engineer
- LLM/Agent Data Scientist

## Cấu trúc tài liệu

- `docs/baseline-v1/`: bản tài liệu cũ (v1), đã được chuyển nguyên trạng vào subfolder
- `docs/deep-dive-v2/`: bản super deep-dive thế hệ 2
- `docs/deep-dive-v3/`: bản **ultra deep-dive (PhD-level)**, có formal model + Mermaid + call-flow theo file/function

## Snapshot deep-dive hiện tại

- Source repo: `https://github.com/openclaw/openclaw`
- Commit: `445c7a65e6d1348f5a64f3ca8ad45369d0ab2027`
- Commit time: `2026-02-23 18:19:23 +0000`

## Quick start

1. Đọc `docs/deep-dive-v3/00_navigator.md`
2. Chọn track theo vai trò
3. Dùng `docs/baseline-v1/` và `docs/deep-dive-v2/` làm tham chiếu evolution

## Quy mô snapshot (ước lượng)

- Total files: ~6,245
- LOC trong `src/`: ~654,679
- TS files toàn repo: ~4,427
- Tests trong `src` (test/e2e/live): ~1,355
- Plugin manifests: 36

## Ghi chú

Bộ tài liệu tập trung vào implementation và kiến trúc runtime. Không thay thế tài liệu vận hành chính thức của OpenClaw.
