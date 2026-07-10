# Bug Report

## Metadata
- Skill: sub2api-summary
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0c04c9eba38e0f7b893af2815cbbee2376e08ccde8a65053c2dbb395dccd6780
- Severity: high
- Occurrence count: 1
- First seen at: 2026-06-28T03:24:59Z
- Last seen at: 2026-06-28T03:24:59Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
payment_dashboard recent_orders are not fully redacted

## Expected Behavior
All collected payment dashboard fields containing user identity data should be redacted before being written to data files.

## Actual Behavior
The payment dashboard collection output includes raw user email values inside recent_orders, despite the skill safety boundary requiring recursive redaction.

## Reproduction Steps
- Run sub2api-summary collection against a site with payment dashboard data.
- Inspect the collected payment_dashboard.json recent_orders entries.

## Evidence
- recent_orders user identity fields remain unredacted in the collected payment dashboard output.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.181 (Claude Code)
  - codex: codex-cli 0.137.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Do not quote or copy recent_orders identity fields; use aggregate payment_dashboard totals and redacted order sample fields for analysis.

## Additional Notes
None
