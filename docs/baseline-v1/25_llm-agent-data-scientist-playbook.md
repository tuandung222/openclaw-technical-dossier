# 25 - LLM Agent Data Scientist Playbook

## Mục Tiêu

Đánh giá và cải thiện chất lượng retrieval, tool-use, routing, và multi-turn outcomes bằng dữ liệu thực.

## Nguồn Dữ Liệu Khả Dụng

- session transcripts
- usage metrics
- queue/latency diagnostics
- cron run logs
- security/audit findings

## Experimental Tracks

### Retrieval Quality

- ablation: vector-only vs hybrid
- tuning vector/text weights
- MMR lambda sweep
- temporal half-life sweep

### Agent Runtime Quality

- fallback effectiveness theo provider
- tool-policy strictness vs task success
- queue congestion vs response latency

### Safety Quality

- approval friction rate
- unsafe-tool request rate
- channel exposure drift detection

## Evaluation Harness Gợi Ý

- tạo offline benchmark từ transcripts đã anonymize
- define gold labels cho retrieval relevance
- build dashboard theo cohort channel/agent/model

## Kết Luận

OpenClaw có đủ telemetry hooks để xây vòng lặp khoa học dữ liệu thực thụ cho agent systems, không chỉ qualitative debugging.
