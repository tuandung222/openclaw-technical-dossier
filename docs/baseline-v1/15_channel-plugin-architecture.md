# 15 - Channel Plugin Architecture

## Runtime Registry

`src/channels/plugins/index.ts` lấy channel plugins từ active plugin registry:

- `listChannelPlugins()`
- `getChannelPlugin(id)`
- normalization + ordering + dedupe

## Channel Plugin Contract

`src/channels/plugins/types.ts` export nhiều adapter types cho:

- auth
- command gating
- outbound
- directory
- mention/threading
- heartbeat/status
- pairing

## Plugin Load Path

`src/plugins/loader.ts`:

1. discover plugin candidates
2. load manifest registry
3. validate config schema
4. instantiate plugin runtime
5. register channels/tools/hooks/methods

## Pattern Trong Extensions

Ví dụ `extensions/telegram/index.ts`:

- khai báo plugin metadata
- inject runtime qua `setTelegramRuntime`
- `api.registerChannel({ plugin })`

## Ý Nghĩa

- Channel integrations là plugin-first, không hardcode toàn bộ trong core.
- Điều này giảm coupling, tăng tốc thêm channel mới.
