# 26 - Risks Tech Debt And Roadmap (Deep)

## Risk register mở rộng

### R1 - Policy complexity opacity

- Triệu chứng: khó giải thích vì sao tool bị deny.
- Impact: debug chậm, dễ chỉnh sai policy.
- Action: policy decision trace + explain API.

### R2 - Plugin trust and runtime coupling

- Triệu chứng: plugin lỗi ảnh hưởng startup/runtime stability.
- Impact: degrade availability/security.
- Action: plugin isolation + stricter load-time validation.

### R3 - Retrieval mode instability

- Triệu chứng: quality dao động khi provider mất và rơi về FTS-only.
- Impact: user-facing inconsistency.
- Action: retrieval mode metrics + fallback quality alerting.

### R4 - Control surface exposure drift

- Triệu chứng: auth/scope/bind config thay đổi nhưng không audit.
- Impact: tăng attack surface.
- Action: mandatory preflight audit + policy baseline checks.

## Technical debt priorities

1. End-to-end policy explainability.
2. Unified observability schema across subsystems.
3. Stronger plugin contract compatibility tooling.
4. Standardized benchmark harness for retrieval/failover.

## 90-day roadmap đề xuất

### Days 0-30

- implement policy traces
- baseline dashboards for queue/fallback/approval
- add security preflight CI stage

### Days 31-60

- plugin conformance suite v1
- retrieval nightly eval pipeline
- fallback decision analytics

### Days 61-90

- adaptive policy recommendations
- automated regression triage for model/routing/tool changes
- hardened deployment profiles for common topologies
