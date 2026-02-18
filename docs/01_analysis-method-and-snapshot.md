# 01 - Analysis Method And Snapshot

## Snapshot Cố Định

- Repo: `openclaw/openclaw`
- Commit: `114736ed1a52de47043d9154e2cf6508a16fe5b6`
- Không phân tích theo HEAD động để tránh drift.

## Phạm Vi Mã Nguồn Được Đọc

Các cụm được đọc trực tiếp từ implementation:

- `src/entry.ts`, `src/index.ts`, `src/runtime.ts`
- `src/gateway/*` (đặc biệt `server.impl.ts`, `server-methods.ts`, `server-methods-list.ts`, `openai-http.ts`)
- `src/agents/*` (đặc biệt `pi-embedded-runner/run.ts`, `pi-tools.ts`, `model-selection.ts`, `model-fallback.ts`)
- `src/memory/*` (đặc biệt `manager.ts`, `hybrid.ts`, `mmr.ts`, `temporal-decay.ts`, `query-expansion.ts`)
- `src/plugins/*`, `src/channels/plugins/*`
- `src/routing/resolve-route.ts`, `src/sessions/send-policy.ts`
- `src/security/audit.ts`, `src/process/command-queue.ts`, `src/cron/service.ts`
- `ui/*` và một số `extensions/*`

## Phương Pháp

1. Khảo sát cấu trúc monorepo và thống kê nhanh (`rg`, `wc`, `find`).
2. Chọn file “orchestrator” ở mỗi subsystem để đọc trước.
3. Theo dấu import sang các module quyết định behavior runtime.
4. Tách tài liệu thành 3 lớp:
   - Kiến trúc tổng thể
   - Luồng runtime chi tiết
   - Playbook theo persona
5. Đóng gói thành bộ 20-30 tài liệu để dễ tái sử dụng.

## Kế Hoạch Triển Khai Tài Liệu

### Giai đoạn 1: Baseline Kiến Trúc

- Bản đồ monorepo
- Lifecycle runtime
- Gateway control plane
- Security boundary

### Giai đoạn 2: Lõi Agent/LLM

- Agent execution pipeline
- Tooling + sandbox + approvals
- Model provider abstraction + failover
- Memory indexing/ranking

### Giai đoạn 3: Hệ Sinh Thái + Vận Hành

- Session routing
- Channel/plugin architecture
- Extension ecosystem
- UI, cron, observability, testing, deployment

### Giai đoạn 4: Playbooks & Roadmap

- Persona-specific guides
- Risk register và đề xuất roadmap

## Giới Hạn

- Không benchmark runtime thực tế trong tài liệu này.
- Không audit sâu mã native trong Android/iOS/macos Swift modules.
- Không thay thế security review chính thức hoặc threat-model formal.
