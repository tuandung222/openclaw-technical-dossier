# 18 - Cron Automation Heartbeat (Deep)

## Cron service composition

`CronService` là façade, còn logic thực ở `src/cron/service/*`:

- `state.ts`
- `ops.ts`
- `jobs.ts`
- `timer.ts`
- `store.ts`

Thiết kế này giảm file khổng lồ và tăng test locality.

## Job lifecycle

- add/update/remove persisted jobs
- compute due windows
- execute in controlled mode (`due` vs `force`)
- record run logs

## Isolated agent mode

`src/cron/isolated-agent/*` cho phép cron runs không trộn trực tiếp với interactive session.

## Heartbeat relationship

Cron và heartbeat cùng tạo background pressure lên queue/runtime. Cần lane planning để tránh ảnh hưởng throughput của chat live.

## Known risk zones

- timer drift dưới tải cao
- duplicate scheduling trong restart race
- delivery target ambiguity khi session metadata thiếu

## Practices

- bật metrics cho `nextRun lag`
- cảnh báo khi `run` thường xuyên timeout
- test regression cho timezone/day-boundary jobs
