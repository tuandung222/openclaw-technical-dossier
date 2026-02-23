# 24 - LLM Engineer Playbook (Deep)

## Khu vực trọng yếu

- model normalization and selection
- failover chain design
- auth profile rotation/cooldown
- prompt-tool interop
- context window pressure management

## Tối ưu failover thực dụng

- đặt primary theo chất lượng
- đặt secondary theo reliability/cost
- log failover reasons chuẩn hóa
- đặt cooldown đủ dài để tránh thrash

## Tool calling reliability

- dùng schemas provider-compatible
- sanitize/normalize tool params trước call
- theo dõi tool error taxonomy theo model/provider

## Context pressure controls

- compaction policy khi overflow
- truncation cho oversized tool outputs
- kiểm tra usage accounting đúng cache token semantics

## Quality KPIs

- successful first-attempt rate
- fallback success rate
- tool-call completion rate
- context-overflow incident rate
