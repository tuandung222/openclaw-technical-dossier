# 10 - Model Provider Abstraction

## Module Lõi

- `src/agents/model-selection.ts`
- `src/agents/models-config.ts`
- `src/agents/models-config.providers.ts`
- `src/providers/*`

## Chuẩn Hóa Provider

`normalizeProviderId()` xử lý alias provider:

- `z.ai` / `z-ai` -> `zai`
- `opencode-zen` -> `opencode`
- `qwen` -> `qwen-portal`
- `kimi-code` -> `kimi-coding`

## Chuẩn Hóa Model

`normalizeModelRef(provider, model)`:

- chuẩn hóa alias model theo provider (vd anthropic/google)
- tự chuyển `openai` sang `openai-codex` khi match prefix codex OAuth models

## Allowlist + Alias Index

- `buildConfiguredAllowlistKeys()` dựng tập model keys hợp lệ.
- `buildModelAliasIndex()` map alias sang model ref thực.
- `resolveModelRefFromString()` hỗ trợ cả `provider/model` lẫn alias.

## Ý Nghĩa Kỹ Thuật

- Là lớp anti-chaos cho đa provider environment.
- Giảm config drift khi user đổi model/provider bằng tên alias.
- Tạo nền tốt cho failover và auth-profile rotation.
