# 21 - Ops Deployment And Release

## Runtime Và Build

- Node requirement: `>=22.12.0`
- Package manager: `pnpm@10.x`
- Build flow: `pnpm build` + `pnpm ui:build`

## Deployment Modes

Trong repo có artifacts cho:

- local source run
- Docker / Podman
- Nix mode
- mobile/mac companion paths

## Gateway Exposure

Gateway hỗ trợ local + remote patterns (tailscale serve/funnel, ssh tunnel) trong docs chính thức.

## Operational Controls

- `openclaw doctor` cho health/config checks
- security audit cho hardening review
- update channel strategy (`stable/beta/dev`)

## Release Hygiene

- protocol schema generation checks
- docs link audit scripts
- extensive CI checks

## Tư Duy Vận Hành

OpenClaw nên được vận hành như một control-plane service có policy và state nhạy cảm, không chỉ là CLI utility.
