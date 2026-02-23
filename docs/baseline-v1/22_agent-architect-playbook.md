# 22 - Agent Architect Playbook

## Mục Tiêu Vai Trò

Thiết kế topology agent đáng tin cậy theo yêu cầu isolation, governance, throughput và extensibility.

## Quyết Định Kiến Trúc Cần Chốt

1. Agent decomposition
2. Session boundary strategy
3. Tool privilege boundaries
4. Channel routing matrix
5. Failover and model governance

## Blueprint Gợi Ý

### Layer 1: Gateway Core

- giữ minimal policy ở global
- bật auth + scope strict
- bật audit checks trong CI preflight

### Layer 2: Agent Domains

- mỗi domain workflow là một agent
- tách workspace rõ theo risk profile
- áp dụng send policy per domain

### Layer 3: Capability Planes

- tools core
- sandboxed tools
- channel action tools
- plugin-specific tools

## Anti-Patterns

- Dồn mọi channel vào một agent/session key.
- Cho phép `allow: ["*"]` mà thiếu deny guard.
- Không version hóa config schema và policy decisions.

## Kiến Trúc Reference

- Route binding theo channel/account/peer.
- Session key chuẩn hóa theo agent scope.
- Fallback policy phân biệt hard-fail và soft-fail.
