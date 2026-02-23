# 20 - Testing And Quality Engineering (Deep)

## Test footprint

Với ~1,355 test files chỉ trong `src`, chất lượng phụ thuộc mạnh vào test discipline.

## Test categories quan sát được

- unit
- integration
- e2e
- live/provider
- browser/ui
- docker environment tests

## CI quality gates

Scripts cho lint/type/build/test/docs/protocol checks tạo baseline khá chặt.

## Deep QA strategies đề xuất

1. Contract tests cho plugin SDK version boundaries.
2. Snapshot tests cho policy explain traces.
3. Chaos tests cho provider failover + auth cooldown.
4. Performance regression tests cho queue latency under channel burst.

## Common regression vectors

- legacy config migration edge cases
- channel-specific message metadata handling
- tool schema compatibility theo provider quirks

## Engineering recommendation

Bất kỳ thay đổi nào ở `agents/gateway/config/security` nên yêu cầu ít nhất:

- unit + e2e proof
- negative tests cho safety behavior
- changelog note rõ risk surface
