# 27 - Formal Verification Roadmap

## Why verification here

OpenClaw có nhiều policy-driven paths nơi bug nhỏ có thể tạo security or correctness regressions lớn.

## Candidate properties for formal methods

- P1: scope authorization soundness
- P2: tool deny non-bypassability
- P3: routing determinism and agent isolation
- P4: queue lane safety under reset/restart

## Suggested approach

### Phase 1 - Model extraction

Trích xuất simplified state machines từ code cho gateway auth, tool policy, routing.

### Phase 2 - Property checking

Dùng model checker/TLA+ style specs cho safety/liveness properties chính.

### Phase 3 - Runtime assertion bridge

Map formal properties thành runtime assertions và property-based tests.

## Expected value

- giảm high-severity regressions
- giảm ambiguity khi refactor policy-heavy modules
- tăng confidence cho remote deployment modes
