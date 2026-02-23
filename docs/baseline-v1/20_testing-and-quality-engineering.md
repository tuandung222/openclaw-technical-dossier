# 20 - Testing And Quality Engineering

## Mật Độ Test

Quan sát snapshot:

- ~1,094 file test/e2e/live trong `src/`
- thêm test ở `test/` và `ui/`

## Test Layering

- Unit tests theo module
- Integration/e2e tests cho gateway methods và flows
- Live tests cho provider-dependent behavior
- Browser tests cho UI

## Quality Toolchain

Từ `package.json`:

- lint: `oxlint`
- format: `oxfmt`
- type/build: `tsdown`, `tsc`
- test: `vitest` + docker suites

## Đặc Điểm Đáng Chú Ý

- Có nhiều regression tests đặt theo issue IDs.
- Test matrix bao gồm docker-based flows.
- Config schema có test coverage riêng dày.

## Khuyến Nghị

- Với extension mới, bắt buộc thêm:
  - contract tests cho plugin registration
  - auth/policy tests
  - e2e route + delivery tests
