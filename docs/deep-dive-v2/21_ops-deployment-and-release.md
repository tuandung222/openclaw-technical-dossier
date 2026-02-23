# 21 - Ops Deployment And Release (Deep)

## Deployment modes

OpenClaw hỗ trợ local-first và remote-hosted patterns, với nhiều đường triển khai:

- source run
- docker/podman
- nix
- native companion apps

## Runtime constraints

- Node >= 22.x
- long-running gateway process
- persistent state directory + config store

## Operational pillars

1. Auth and exposure policy (bind/auth/tailscale/proxy)
2. Backup and state hygiene
3. Monitoring and diagnostics
4. Update channel governance

## Release hygiene

- protocol generation checks
- docs link audit
- multi-suite tests
- changelog maintenance

## Ops anti-patterns

- chạy gateway public mà thiếu password/token policy nghiêm
- bỏ qua security audit sau config thay đổi lớn
- không quan sát queue lag/approval lag trong production
