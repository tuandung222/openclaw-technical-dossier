# 12 - Memory Subsystem Architecture (Deep)

## Orchestrator class

`MemoryIndexManager` chịu trách nhiệm end-to-end:

- provider selection
- DB setup/schema
- watcher scheduling
- sync operations
- query execution

## Storage model

Tables chính:

- `chunks_vec` cho vector retrieval
- `chunks_fts` cho keyword retrieval
- `embedding_cache` cho cost/perf optimization

## Provider fallbacks

Nếu embedding provider unavailable:

- chuyển sang FTS-only mode
- query expansion được bật để giảm quality drop

## Sync sources

Nguồn dữ liệu memory có thể gồm:

- memory markdown files
- session transcript updates
- extra paths theo config

## Runtime behavior

Manager có các flag và timers:

- dirty flags cho lazy sync
- watcher debounce
- session warmup sync
- periodic interval sync

## Scaling concern

Cache key gắn với `agentId + workspace + settings`, nếu deployment nhiều agent/workspace có thể tạo nhiều index manager instances.
