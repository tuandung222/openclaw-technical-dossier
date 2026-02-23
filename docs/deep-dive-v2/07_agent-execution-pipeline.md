# 07 - Agent Execution Pipeline (Deep)

## Entrypoint

`runEmbeddedPiAgent(params)` trong `src/agents/pi-embedded-runner/run.ts`.

## Control flow breakdown

### Phase A - Queue & lane resolution

- resolve session lane + global lane
- enqueue nested tasks để kiểm soát concurrent pressure

### Phase B - Context and workspace resolution

- resolve workspace từ sessionKey/agentId/config
- fallback logging nếu phải rơi về workspace mặc định

### Phase C - Model resolution hooks

- chạy `before_model_resolve`
- chạy compatibility path `before_agent_start`
- apply provider/model overrides nếu hook trả về

### Phase D - Run attempts

- resolve model/auth profile
- execute attempt
- classify lỗi (rate limit, billing, auth, overflow, timeout)
- fallback sang candidate tiếp theo khi hợp lệ

### Phase E - Post-processing

- normalize usage
- tool result truncation nếu oversized
- optional compaction khi context pressure cao

## Robustness patterns

- explicit abort-vs-timeout differentiation
- cached usage accounting tránh context-window inflation bug
- auth-profile good/fail/cooldown updates

## Engineering notes

Đây là module có coupling cao nhất giữa model, tool, memory và queue. Refactor nên làm theo seams đã có (`run/attempt`, `run/payloads`, `model.ts`, `lanes.ts`).
