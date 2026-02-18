# 07 - Agent Execution Pipeline

## Điểm Vào Lõi

- `src/agents/pi-embedded-runner/run.ts`
- Hàm chính: `runEmbeddedPiAgent(params)`

## Pipeline Mức Cao

1. Resolve lane (session lane + global lane) để queue command.
2. Resolve workspace thực tế theo session/agent context.
3. Resolve provider/model (có hook override trước model resolve).
4. Chuẩn bị toolset + policy + prompt payloads.
5. Chạy attempt loop với failover handling.
6. Ghi usage/tokens và chuẩn hóa stream output.
7. Compaction/truncation nếu có overflow/tool payload quá lớn.

## Queue Discipline

- Execution đi qua `enqueueCommandInLane`.
- Mục tiêu: tránh interleaving output/input giữa các phiên nhạy cảm.
- Cho phép limited parallelism theo lane policy.

## Hook Integration

Runner gọi global hooks như:

- `before_model_resolve`
- fallback `before_agent_start` (legacy compatibility)

Điểm quan trọng: hook có thể override provider/model trước model resolution.

## Reliability Controls

- Context window guard (`evaluateContextWindowGuard`).
- Fallback classification cho auth/billing/rate-limit/overflow.
- Usage accumulator xử lý cache token field cẩn thận để tránh context-size inflation.

## Kết Luận

Đây là pipeline thiên về production robustness hơn là demo simplicity: queueing, fallback, hook layering, token accounting đều được làm khá kỹ.
