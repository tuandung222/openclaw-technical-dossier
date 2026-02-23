# 11 - Model Failover And Auth Profiles

## Failover Engine

`src/agents/model-fallback.ts` điều phối fallback candidates theo thứ tự:

1. Primary đã normalize
2. Fallbacks từ config (nếu có)
3. Default configured model (tuỳ context)

## Candidate Governance

- Deduplicate theo `provider/model` key.
- Có thể enforce allowlist cho fallback candidates.
- Phân loại failure reason (timeout, auth, rate-limit, billing, overflow).

## Auth Profiles

`src/agents/auth-profiles/*` quản lý:

- profile store
- usage stats
- cooldown window
- order resolution
- OAuth/API-key credentials

## Cooldown Strategy

- Profile fail có cooldown thay vì loại vĩnh viễn.
- Có probe throttle để thử lại primary hợp lý.
- Tránh “thrashing” giữa profile lỗi liên tục.

## Engineering Implication

- Failover không chỉ là model list; nó là tổ hợp model + credential health.
- Độ ổn định phụ thuộc chất lượng policy trong auth profile store.
