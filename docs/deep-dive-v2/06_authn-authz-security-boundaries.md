# 06 - AuthN AuthZ Security Boundaries (Deep)

## Security model đa lớp

OpenClaw dùng layered controls:

1. transport auth (gateway)
2. method-level authz (role/scope)
3. session/channel policy
4. tool policy pipeline
5. sandbox/exec approval

Không có lớp nào đủ một mình.

## Filesystem hardening checks

`src/security/audit.ts` + `audit-fs.ts` kiểm tra:

- state dir world/group writable
- config file readable/writable bởi user khác
- symlink boundaries

Đây là điểm ít hệ agent khác làm kỹ.

## Exposure risk checks

Audit còn đánh giá kết hợp:

- gateway bind mode
- tailscale serve/funnel
- auth mode/token/password
- trusted proxies
- dangerous HTTP tool enables

## Channel security

`collectChannelSecurityFindings` bổ sung kiểm tra DM policy/allowlist/pairing posture từng channel.

## Security debt thường gặp

- policy drift giữa config global và agent overrides
- quá tin tưởng plugin config từ nguồn ngoài
- mở remote access nhưng thiếu scope segmentation

## Hardening priorities

1. enforce baseline policy templates
2. bật security audit trong CI pre-deploy
3. log và cảnh báo scope violations theo thời gian thực
