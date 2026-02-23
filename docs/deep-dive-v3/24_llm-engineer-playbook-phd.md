# 24 - LLM Engineer Playbook (PhD)

## Core thesis

LLM quality trong production agent systems là kết quả của pipeline governance, không chỉ model capability.

## Priority workstreams

- model normalization correctness
- fallback decision quality
- tool-calling compatibility
- context pressure management
- retrieval alignment

## Experimental protocol

- define hypotheses per subsystem
- run controlled A/B with fixed workload slices
- track confidence intervals, not only mean improvement
- preserve reproducible artifacts

## Recommended metrics

- first-attempt success probability
- fallback chain depth distribution
- tool schema failure rate
- context overflow incidence
- retrieval contribution uplift
