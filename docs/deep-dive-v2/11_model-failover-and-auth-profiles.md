# 11 - Model Failover And Auth Profiles (Deep)

## Failover control loop

`resolveFallbackCandidates()` tạo danh sách chạy thử theo thứ tự đã chuẩn hóa.

Loop failover cần xử lý:

- error classification
- abort policy
- profile cooldown state
- primary reprobe cadence

## Auth profile state machine

Auth profile có trạng thái vận hành:

- healthy
- recently failed (cooldown)
- reusable sau expiry

`auth-profiles/usage.ts` duy trì timestamp + reason để order resolver ra quyết định tốt hơn.

## Probe throttling

Module failover có throttle key theo `provider + agentDir` để tránh probe storm.

## Error semantics

Phân biệt quan trọng:

- abort do user (không fallback vô nghĩa)
- timeout/transient failures (fallback hợp lý)
- auth/billing failures (thường cần profile/provider khác)

## Engineering recommendations

- log structured fallback trace cho từng attempt
- export metrics theo reason class
- cảnh báo khi fallback chain bị cạn thường xuyên
