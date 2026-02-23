# 15 - Channel Plugin Architecture (Deep)

## Registry flow

`listChannelPlugins()` lấy từ active plugin registry, dedupe theo id và sort theo:

- explicit plugin meta order
- fallback order từ channel registry

## Plugin runtime coupling

Channel plugin thường đăng ký theo pattern:

- set runtime reference
- register channel adapters
- expose gateway methods (nếu có)

## Adapter surfaces

Các adapter quan trọng trong `types.core/adapters`:

- outbound/messaging
- threading/mentions
- auth/security/pairing
- directory/status
- command/elevated handling

## Design strengths

- tách channel behavior khỏi core compile-time wiring
- cho phép release channel-specific fixes nhanh hơn
- giúp testing per-channel contracts độc lập

## Design risks

- plugin quality variance có thể gây runtime instability
- contract drift nếu plugin dùng API cũ

Mitigation: versioned plugin SDK contracts + loader validations + richer conformance tests.
