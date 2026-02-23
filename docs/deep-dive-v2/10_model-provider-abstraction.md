# 10 - Model Provider Abstraction (Deep)

## Canonicalization layer

`src/agents/model-selection.ts` là canonicalization core:

- normalize provider aliases
- normalize model IDs theo provider
- parse `provider/model` hoặc alias
- build keys cho allowlist enforcement

## Alias and compatibility handling

- Anthropic model alias mapping (opus/sonnet aliases)
- Google model normalization
- OpenAI Codex OAuth prefix detection -> route sang `openai-codex`

## Config bridge

Layer này ghép giữa:

- user-facing config (friendly/legacy values)
- runtime provider contracts (canonical ids)

## Why this matters

Không canonicalization, fallback/policy/cache keys sẽ bị phân mảnh và gây behavior không quyết định được.

## Extension implications

Khi thêm provider mới cần đảm bảo:

- alias policy rõ ràng
- normalized key stability
- compatible with allowlist and auth profile lookup
