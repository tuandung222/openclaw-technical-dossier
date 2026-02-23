# 05 - Gateway Method Taxonomy (Deep)

## Method families

### Read-only operational

`health`, `status`, `logs.tail`, `usage.*`, `models.list`, `agents.list`, ...

### Mutating control

`config.*`, `wizard.*`, `sessions.patch/reset/delete`, `cron.*`, `skills.install/update`, ...

### Execution triggering

`agent`, `chat.send`, `send`, `node.invoke`, `browser.request`, ...

### Approval and pairing

`exec.approval.*`, `node.pair.*`, `device.pair.*`

## Authorization matrix

Authorize theo:

- role: `operator` vs `node`
- scopes: read/write/admin/approvals/pairing

Design này cho phép cùng một transport nhưng least-privilege theo client persona.

## Handler dispatch path

- authorize method
- resolve core/extra handler
- normalize params/context
- execute async handler
- respond with structured error shape nếu fail

## Event taxonomy

`GATEWAY_EVENTS` bao gồm agent/chat/presence/cron/health/approval/pairing và heartbeat categories.

## Operational implication

- Có thể xây policy gateway-side dựa trên method classes.
- Có thể audit hành vi client theo scope usage chứ không chỉ theo endpoint hit.
