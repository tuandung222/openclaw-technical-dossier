# 12 - Memory Subsystem Architecture

## Memory Manager

`MemoryIndexManager` trong `src/memory/manager.ts` là orchestration center cho:

- indexing
- embedding
- vector search
- keyword search
- sync lifecycle

## Data Planes

- Vector plane: bảng `chunks_vec`
- FTS plane: bảng `chunks_fts`
- Cache plane: bảng `embedding_cache`

DB backend dùng SQLite, vector extension qua `sqlite-vec` (`src/memory/sqlite-vec.ts`).

## Provider Layer

`createEmbeddingProvider()` có thể chọn:

- openai
- gemini
- voyage
- local/auto/fallback

## Sync & Watch

Manager duy trì:

- watcher file memory
- session transcript listener
- interval sync
- dirty flags (`dirty`, `sessionsDirty`)

## Search Modes

- Vector-only
- Hybrid (vector + FTS)
- FTS-only fallback khi embedding provider unavailable

## Lưu Ý Vận Hành

- Memory subsystem có cache key phụ thuộc config + workspace + agent.
- Nếu config đổi, manager cache có thể phải rebuild để tránh stale index behavior.
