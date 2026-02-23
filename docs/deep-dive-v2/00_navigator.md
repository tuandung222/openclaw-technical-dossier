# Deep Dive V2 - Navigator

## Mục đích của bộ V2

Bộ `deep-dive-v2` mở rộng bản baseline theo hướng implementation-first:

- bám vào snapshot code mới nhất đã pull
- chỉ rõ luồng runtime, dependency, boundary và failure mode
- tách hướng đọc theo persona kỹ thuật

## Snapshot được dùng

- Repository: `openclaw/openclaw`
- Commit: `445c7a65e6d1348f5a64f3ca8ad45369d0ab2027`
- Commit time: `2026-02-23 18:19:23 +0000`

## Reading Tracks

### Track A - System Architecture (Agent Architect)

1. `01_analysis-method-and-snapshot.md`
2. `02_monorepo-map.md`
3. `04_gateway-control-plane.md`
4. `05_gateway-method-taxonomy.md`
5. `06_authn-authz-security-boundaries.md`
6. `14_session-routing-isolation.md`
7. `22_agent-architect-playbook.md`
8. `26_risks-tech-debt-and-roadmap.md`

### Track B - Runtime Engineering (AI Agent Engineer)

1. `03_boot-and-runtime-lifecycle.md`
2. `07_agent-execution-pipeline.md`
3. `08_tooling-layer-and-policy.md`
4. `09_sandbox-and-exec-approvals.md`
5. `15_channel-plugin-architecture.md`
6. `16_extension-ecosystem-map.md`
7. `23_ai-agent-engineer-playbook.md`

### Track C - Model & Memory (LLM Engineer)

1. `10_model-provider-abstraction.md`
2. `11_model-failover-and-auth-profiles.md`
3. `12_memory-subsystem-architecture.md`
4. `13_memory-ranking-algorithms.md`
5. `24_llm-engineer-playbook.md`

### Track D - Evaluation & Quality (LLM/Agent Data Scientist)

1. `12_memory-subsystem-architecture.md`
2. `13_memory-ranking-algorithms.md`
3. `19_observability-and-diagnostics.md`
4. `20_testing-and-quality-engineering.md`
5. `25_llm-agent-data-scientist-playbook.md`

## Cách đọc nhanh theo câu hỏi

- Gateway control surface có gì? -> `04`, `05`, `17`
- Làm sao agent chạy ổn định khi provider lỗi? -> `07`, `10`, `11`
- Memory retrieval logic nằm ở đâu? -> `12`, `13`
- Chính sách bảo mật chạy ở lớp nào? -> `06`, `08`, `09`
- Nên thiết kế monitoring gì? -> `19`, `20`, `21`
