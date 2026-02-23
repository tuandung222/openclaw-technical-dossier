# 00 - Navigator

## Mục tiêu

Giúp bạn chọn lộ trình đọc nhanh theo vai trò và câu hỏi kỹ thuật cần trả lời.

## Reading Map Theo Vai Trò

### Agent Architect

- `02_monorepo-map.md`
- `04_gateway-control-plane.md`
- `06_authn-authz-security-boundaries.md`
- `14_session-routing-isolation.md`
- `22_agent-architect-playbook.md`
- `26_risks-tech-debt-and-roadmap.md`

### AI Agent Engineer

- `03_boot-and-runtime-lifecycle.md`
- `07_agent-execution-pipeline.md`
- `08_tooling-layer-and-policy.md`
- `09_sandbox-and-exec-approvals.md`
- `15_channel-plugin-architecture.md`
- `23_ai-agent-engineer-playbook.md`

### LLM Engineer

- `10_model-provider-abstraction.md`
- `11_model-failover-and-auth-profiles.md`
- `12_memory-subsystem-architecture.md`
- `13_memory-ranking-algorithms.md`
- `24_llm-engineer-playbook.md`

### LLM/Agent Data Scientist

- `12_memory-subsystem-architecture.md`
- `13_memory-ranking-algorithms.md`
- `19_observability-and-diagnostics.md`
- `20_testing-and-quality-engineering.md`
- `25_llm-agent-data-scientist-playbook.md`

## Câu Hỏi Chính Và Tài Liệu Trả Lời

- Hệ thống khởi động thế nào? -> `03`
- Gateway xử lý request/event ra sao? -> `04`, `05`
- Bảo mật và phân quyền cụ thể thế nào? -> `06`, `09`
- Luồng thực thi agent ra sao? -> `07`
- Tool policy hoạt động thế nào? -> `08`
- Model fallback / auth profile được quản lý thế nào? -> `10`, `11`
- Memory retrieval stack có gì đặc biệt? -> `12`, `13`
- Session isolation và route binding hoạt động ra sao? -> `14`
- Muốn thêm channel/plugin mới làm như thế nào? -> `15`, `16`, `23`

## Dependency Graph (đọc nhanh)

1. `01` -> ngữ cảnh và phương pháp
2. `02-06` -> nền tảng platform
3. `07-16` -> implementation lõi
4. `17-21` -> UI, ops, quality
5. `22-26` -> hành động theo vai trò + roadmap
