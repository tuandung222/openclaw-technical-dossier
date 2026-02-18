# 05 - Gateway Method Taxonomy

## Method Inventory

`src/gateway/server-methods-list.ts` liệt kê base methods và gateway events.

Nhóm method chính:

- Health/Status: `health`, `status`, `usage.*`, `logs.tail`
- Config/Wizard: `config.*`, `wizard.*`
- Agent/Session: `agent`, `agent.wait`, `sessions.*`, `chat.*`
- Channel/Send: `send`, `channels.status`, `channels.logout`
- Nodes/Devices: `node.*`, `device.*`
- Cron: `cron.*`
- Skills/Models: `skills.*`, `models.list`
- Security approvals: `exec.approval.*`, `exec.approvals.*`

## Authorization Layer

`src/gateway/server-methods.ts` định nghĩa authorization theo role/scope.

Role:

- `operator`
- `node`

Scope chính:

- `operator.read`
- `operator.write`
- `operator.admin`
- `operator.approvals`
- `operator.pairing`

## Pattern Xử Lý Request

1. Authorize method theo role/scope.
2. Resolve handler từ core + extra handlers (plugin).
3. Validate unknown methods với lỗi chuẩn.
4. Gọi handler với context đã chuẩn hóa.

## Ý Nghĩa Thiết Kế

- Có separation giữa control API và capability API.
- Node role bị giới hạn method cứng, giảm blast radius.
- Scope-driven governance giúp triển khai remote gateway an toàn hơn.
