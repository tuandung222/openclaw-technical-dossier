# 18 - Cron Automation Heartbeat

## Cron Service API

`src/cron/service.ts` expose lớp `CronService` với các operations:

- `start/stop/status`
- `list/add/update/remove`
- `run`
- `wake`

Implementation tách sang `src/cron/service/ops.ts` và các module state/jobs/timer/store.

## Design Points

- Tách state + ops giúp testability cao.
- Có isolated-agent mode cho cron workflows.
- Có run log và migration handling cho store.

## Gateway Integration

Gateway methods liên quan:

- `cron.list`
- `cron.status`
- `cron.add`
- `cron.update`
- `cron.remove`
- `cron.run`
- `cron.runs`

## Heartbeat Linkage

Cron và heartbeat đều là nguồn event background; cần quản lý queue fairness để không starve agent interactive traffic.

## Gợi Ý Kỹ Thuật

- Nên phân lane riêng cho cron-heavy workloads.
- Cần quan sát command queue depth và cron lag metrics khi scale.
