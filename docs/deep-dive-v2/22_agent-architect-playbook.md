# 22 - Agent Architect Playbook (Deep)

## Mục tiêu kiến trúc

Thiết kế hệ agent vừa linh hoạt vừa kiểm soát được risk:

- isolation
- policy clarity
- evolvability
- operability

## Decision matrix

### Agent partitioning

Phân tách theo domain và risk profile, không chỉ theo channel.

### Session boundary

Chọn dm scope + route bindings sao cho tránh context bleed.

### Tool governance

Dùng policy pipeline theo tier (global -> provider -> agent -> group).

### Model governance

Định nghĩa fallback policy và auth profiles theo SLA của từng workflow.

## Architecture blueprint

- Control plane: gateway hardened, scope-based clients
- Execution plane: agent lanes + sandbox + approvals
- Knowledge plane: memory hybrid retrieval + observability
- Integration plane: plugins/channel adapters với conformance checks

## Review checklist cho architecture changes

1. Có thay đổi boundary nào giữa trust zones không?
2. Có tăng implicit privilege ở tool/message flows không?
3. Có telemetry đủ để detect regression không?
4. Có rollback-safe path không?
