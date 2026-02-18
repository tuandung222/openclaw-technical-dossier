# OpenClaw Technical Dossier

Bộ tài liệu này phân tích mã nguồn OpenClaw ở mức kiến trúc và implementation để phục vụ 4 nhóm độc giả chính:

- Agent Architect
- AI Agent Engineer
- LLM Engineer
- LLM/Agent Data Scientist

## Snapshot được phân tích

- Repository gốc: `https://github.com/openclaw/openclaw`
- Commit: `114736ed1a52de47043d9154e2cf6508a16fe5b6`
- Ngày commit: `2026-02-18 00:09:51 -0800`

## Quy mô mã nguồn (ước lượng từ snapshot)

- Tổng file: ~5,640
- Tổng LOC trong `src/`: ~569,432
- File TypeScript toàn repo: ~3,891
- Tài liệu Markdown toàn repo: ~765
- File test trong `src/` (pattern `.test/.e2e/.live`): ~1,094
- Extension plugin khai báo `openclaw.plugin.json`: 36

## Cách dùng bộ tài liệu

1. Bắt đầu với `docs/00_navigator.md`
2. Đọc `docs/01_analysis-method-and-snapshot.md` để hiểu phạm vi và phương pháp
3. Đi theo track theo vai trò:
   - Architect: `22 -> 26`
   - Agent Engineer: `23 + 07 + 08 + 09 + 15`
   - LLM Engineer: `24 + 10 + 11 + 12 + 13`
   - Data Scientist: `25 + 12 + 13 + 19 + 20`

## Cấu trúc

- `docs/00-21`: nền tảng kỹ thuật theo subsystem
- `docs/22-25`: playbook theo persona
- `docs/26`: rủi ro, nợ kỹ thuật, roadmap

## Lưu ý

Bộ tài liệu này thiên về kỹ thuật phần mềm và vận hành agent platform, không thay thế tài liệu chính thức của OpenClaw.
