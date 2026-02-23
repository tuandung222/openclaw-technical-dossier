# 13 - Memory Ranking Algorithms

## Hybrid Merge

`mergeHybridResults()` (`src/memory/hybrid.ts`) kết hợp:

- vector score
- text (BM25 normalized) score
- trọng số `vectorWeight`, `textWeight`

## BM25 Normalization

`bm25RankToScore(rank) = 1 / (1 + rank)`

Ý nghĩa:

- rank thấp (tốt hơn) -> score cao hơn
- scale đơn giản cho weighted fusion

## MMR Re-ranking

`src/memory/mmr.ts`:

- công thức MMR: `lambda * relevance - (1-lambda) * maxSimilarity`
- similarity dùng Jaccard trên token sets
- `enabled` mặc định false (opt-in)

## Temporal Decay

`src/memory/temporal-decay.ts`:

- decay multiplier theo half-life
- ưu tiên recency khi bật
- với memory “evergreen” (`MEMORY.md` hoặc topic file), không decay

## Query Expansion (FTS Fallback)

`src/memory/query-expansion.ts`:

- tách keyword từ câu hội thoại mơ hồ
- stop words cho EN/ZH
- xử lý tokenization mixed-language

## Cho Data Scientist

- Có đủ hook để làm ablation:
  - bật/tắt MMR
  - tuning lambda
  - tuning half-life
  - tuning weight vector/text
- Đây là điểm phù hợp để thiết kế offline retrieval eval suite.
