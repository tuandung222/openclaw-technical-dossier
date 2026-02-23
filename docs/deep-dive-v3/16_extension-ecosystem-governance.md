# 16 - Extension Ecosystem Governance

## Governance problem

Ecosystem lớn (36 manifests) tạo trade-off:

- tốc độ mở rộng capability
- tăng attack and maintenance surface

## Plugin classes and control intensity

- Class A (auth bridge): highest scrutiny
- Class B (capability/memory/voice): high scrutiny
- Class C (thin channel wrappers): medium scrutiny

## Recommended governance matrix

- static checks (manifest/schema/path safety)
- dependency risk scanning
- runtime conformance tests
- periodic security review cadence

## Change control policy

Mỗi plugin release nên có:

1. declared risk class
2. compatibility statement với plugin SDK version
3. rollback instructions

## Outcome metric

`Plugin Reliability Index = success_rate * conformance_score * security_score`
