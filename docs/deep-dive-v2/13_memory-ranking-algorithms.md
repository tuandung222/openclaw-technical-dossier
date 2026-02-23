# 13 - Memory Ranking Algorithms (Deep)

## Hybrid fusion pipeline

`mergeHybridResults()` kết hợp:

- vector candidates
- keyword candidates
- weighted score fusion
- optional temporal decay
- optional MMR rerank

## MMR implementation choices

- similarity: Jaccard token similarity
- lambda clamp về [0,1]
- normalization score trước khi tính MMR
- tie-break bằng score gốc

Trade-off: dễ hiểu, deterministic, rẻ tính toán; đổi lại semantic similarity chưa sâu như embedding-level novelty.

## Temporal decay semantics

- half-life configurable
- dated memory path parse (`memory/YYYY-MM-DD.md`)
- evergreen memory files không decay
- fallback mtime nếu không parse được date từ path

## FTS query expansion

- stopword filters EN/ZH
- token heuristics cho multilingual input
- dùng khi vector provider không khả dụng

## Evaluation hints

Để tuning:

- giữ riêng metric quality cho từng mode (vector/hybrid/fts-only)
- theo dõi overlap giữa top-k trước/sau MMR
- đo stability theo thời gian khi bật temporal decay
