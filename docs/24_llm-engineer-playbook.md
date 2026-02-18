# 24 - LLM Engineer Playbook

## Trọng Tâm

Tối ưu model selection, prompting, fallback reliability và tool calling compatibility.

## Checklist Thiết Kế

- Chuẩn hóa provider/model IDs trước khi dùng.
- Dùng alias mapping cho UX nhưng persist normalized refs.
- Thiết kế fallback list explicit theo cost/latency/risk.
- Thiết kế auth profile cooldown để giảm retry storms.

## Prompt And Tool Interop

- theo dõi provider quirks (Claude/Gemini/OpenAI variants)
- chuẩn hóa schema parameters trước tool call
- bảo vệ context window bằng compaction + truncation strategy

## Memory-Aware Inference

- bật hybrid retrieval nếu recall là critical
- thử MMR khi diversity trong context quan trọng
- thử temporal decay cho workflow time-sensitive

## Đo Lường Nên Có

- fallback hit-rate
- auth profile failure-rate
- tool call success-rate theo provider/model
- response quality regression theo model channel mix

## Khuyến Nghị

Thiết kế “model policy as code” thay vì chỉnh ad-hoc trong config runtime.
