# 16 - Extension Ecosystem Map (Deep)

## Ecosystem snapshot

- 36 extension manifests
- trải rộng channel integrations, auth bridges, memory, voice, diagnostics

## Pattern taxonomy

### Thin channel wrappers

Ví dụ telegram/discord: map runtime + register channel plugin, config schema tối giản.

### Capability plugins

Ví dụ memory-lancedb, voice-call: chứa logic nặng hơn (db/embedding/media pipelines).

### Auth/provider bridge plugins

Ví dụ portal auth plugins: dùng để nối OAuth/token flows với provider ecosystems.

## Security posture per extension type

- thin wrappers: risk chủ yếu ở message parsing/delivery policy
- capability plugins: risk ở external libs và data handling
- auth bridges: risk ở credential flow và storage

## Governance recommendations

1. phân cấp trust level cho plugin categories
2. bắt buộc contract tests cho critical plugins
3. audit dependencies định kỳ cho capability/auth plugins
