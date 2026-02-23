# 21 - Ops SRE Reliability Blueprint

## Reliability objectives

- high control-plane availability
- bounded response latency for interactive sessions
- safe degradation under provider/channel failures

## SLO suggestions

- Gateway availability SLO
- Agent response latency SLO per channel class
- Approval turnaround SLO
- Retrieval success-rate SLO

## Runbook structure

1. Detect (alerts/logs)
2. Diagnose (trace by run/session)
3. Contain (policy knobs/fallback toggles)
4. Recover (service/plugin/provider restoration)
5. Learn (post-incident updates)

## Capacity signals

- queue depth by lane
- active run counts
- cron lag
- plugin load failures

## Operational anti-fragility

- regular chaos drills
- controlled failover game-days
- audit-driven config baselines
