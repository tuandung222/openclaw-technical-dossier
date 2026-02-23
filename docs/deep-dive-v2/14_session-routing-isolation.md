# 14 - Session Routing Isolation (Deep)

## Route engine

`resolve-route.ts` nhận context inbound và xuất:

- `agentId`
- `sessionKey`
- `mainSessionKey`
- `matchedBy`

## Match dimensions

- channel
- accountId
- peer / parentPeer
- guild/team
- member roles

## Caching strategy

Có evaluated-binding cache theo `cfg + channel + account` để giảm cost parse rules liên tục.

## Session key semantics

- agent prefix để tránh cross-agent collision
- helper strip prefix phục vụ rule matching tương thích legacy
- DM scope variants cho isolation granularity

## Send policy resolution

`resolveSendPolicy()` ưu tiên:

1. session entry override
2. rule-based policy
3. default fallback

Rule match có rawKeyPrefix + normalized keyPrefix để tăng tính khớp trong migration scenarios.

## Failure modes

- binding quá rộng -> agent bleed giữa domain
- key format drift -> send policy match sai
- thiếu channel/chatType metadata -> rơi vào default nguy hiểm
