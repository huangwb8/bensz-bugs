# Bug Report

## Metadata
- Skill: sub2api-summary
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 48f00a0ee28594b5e704d13b3501eb76f4efb58e0ae11481cc9b98f1c43b1bde
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-05-02T16:16:45Z
- Last seen at: 2026-05-02T16:16:45Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
collector lacks browser-like User-Agent and can be blocked by Cloudflare 1010

## Expected Behavior
The read-only collector should be robust against common edge-layer bot signature checks when querying an authorized sub2api site.

## Actual Behavior
The default urllib collector received HTTP 403 Cloudflare 1010 Access denied on all endpoints until a browser-like User-Agent and related headers were added.

## Reproduction Steps
- Use an authorized sub2api site protected by Cloudflare browser-signature rules.
- Run collect_sub2api_data.py with valid SUB2API_BASE_URL and SUB2API_ADMIN_API_KEY.

## Evidence
- HTTP 403 Cloudflare error 1010: site owner has blocked access based on browser signature.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.4.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.124.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Use browser-like Accept/User-Agent/Origin/Referer headers for read-only collection.

## Additional Notes
None
