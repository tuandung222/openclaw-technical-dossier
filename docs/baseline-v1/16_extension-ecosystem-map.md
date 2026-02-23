# 16 - Extension Ecosystem Map

## Kích Thước

Hiện có 36 extension plugin manifests.

## Nhóm Extension Chính

### Messaging Channels

- `telegram`, `discord`, `slack`, `signal`, `line`, `googlechat`, `msteams`, `whatsapp`, `zalo`, `zalouser`, `matrix`, `irc`, `mattermost`, `feishu`, `nextcloud-talk`, `bluebubbles`, `imessage`, `tlon`, `twitch`, `nostr`

### Memory/LLM/Auth Utilities

- `memory-core`, `memory-lancedb`, `llm-task`, `copilot-proxy`, `google-gemini-cli-auth`, `google-antigravity-auth`, `minimax-portal-auth`, `qwen-portal-auth`

### Runtime Capability/Platform

- `voice-call`, `talk-voice`, `phone-control`, `thread-ownership`, `diagnostics-otel`, `device-pair`, `shared`, `lobster`, `open-prose`

## Cấu Trúc Extension Điển Hình

- `openclaw.plugin.json` cho metadata + config schema entry
- `index.ts` export plugin object
- thư mục `src/` chứa channel/runtime logic

## Case Study: `memory-lancedb`

Plugin này cho thấy một hướng mở rộng sâu:

- vector store external (LanceDB)
- embeddings qua OpenAI
- recall/capture hooks
- prompt-injection filtering cho memory context

## Kết Luận

Ecosystem extension của OpenClaw đủ rộng để xem như một “agent platform kernel + plugin operating model”.
