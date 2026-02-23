# 02 - Monorepo Map (Deep)

## Monorepo topology

Các workspace chính:

- root core runtime
- `ui` control interface
- `extensions/*` plugin ecosystem
- `packages/*` bot flavors

Tổng thể hoạt động như một product platform hơn là một thư viện đơn.

## Density theo subsystem (src)

Top hiện tại theo số file:

- `agents`: 638
- `commands`: 296
- `infra`: 294
- `gateway`: 280
- `cli`: 253
- `auto-reply`: 226
- `config`: 183
- `channels`: 134

Insight: complexity không chỉ ở inference; phần control/ops và integration rất lớn.

## Kiểu artifact

- TS chiếm đa số tuyệt đối -> runtime logic tập trung ở Node layer
- Swift/Kotlin đáng kể -> native surfaces quan trọng cho iOS/Android/macOS
- Shell scripts lớn -> lifecycle build/test/deploy được automation hóa mạnh

## Module responsibilities map

- `src/entry.ts`, `src/index.ts`: bootstrap + env/runtime safety
- `src/gateway/*`: control plane (WS + HTTP)
- `src/agents/*`: agent loop, model/tool orchestration
- `src/memory/*`: retrieval/indexing/embedding stack
- `src/plugins/*`: plugin runtime/loader/contracts
- `src/security/*`: audit/hardening checks
- `src/process/*`: queue, execution control

## Architectural characterization

OpenClaw có hình thái:

- Local-first control plane
- Multi-channel agent runtime
- Plugin-extensible capability fabric
- Policy-heavy execution platform
