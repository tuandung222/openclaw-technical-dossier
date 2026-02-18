# 14 - Session Routing Isolation

## Route Resolution

`src/routing/resolve-route.ts` quyết định agent + sessionKey theo input:

- channel
- accountId
- peer
- guild/team context
- role constraints

## Matching Priority (thực tế)

Các dạng match được hỗ trợ:

- peer
- parent peer fallback
- guild + roles
- guild
- team
- account
- channel
- default

## Session Key Strategy

- Agent-scoped key format giúp tách session theo agent.
- Có helper strip prefix để rule matching linh hoạt.
- `buildAgentSessionKey()` hỗ trợ DM scope variants.

## Send Policy

`src/sessions/send-policy.ts`:

- override per session entry (`allow`/`deny`)
- rule-based match theo channel/chatType/key prefix
- default fallback policy

## Isolation Takeaway

- Isolation là tổ hợp route + session key + send policy.
- Nếu route sai, isolation hỏng dù model/tool policy đúng.
- Thiết kế hiện tại đủ linh hoạt cho multi-agent multi-channel deployment.
