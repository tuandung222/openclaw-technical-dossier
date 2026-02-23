# 25 - LLM Agent Data Scientist Playbook (Deep)

## Experiment domains

### Retrieval science

- vector vs hybrid vs fts-only
- MMR on/off + lambda sweep
- temporal decay half-life sweep

### Runtime science

- fallback behavior by provider/channel
- approval friction vs task completion
- queue pressure vs response quality/latency

### Safety science

- deny-rate theo tool category
- channel exposure risk indicators
- anomaly detection trên auth/profile failures

## Data pipeline khuyến nghị

1. Thu transcript/usage/log events (đã anonymize).
2. Xây label protocol cho relevance/tool-success/safety.
3. Dựng offline eval benchmarks cố định.
4. Chạy nightly regression và publish diff.

## Experimental rigor

- lock snapshot code + config
- report confidence intervals
- lưu artifact cho reproducibility

## Deliverables hữu ích cho engineering

- model fallback recommendation table
- retrieval tuning presets theo workload
- safety threshold recommendations cho production profiles
