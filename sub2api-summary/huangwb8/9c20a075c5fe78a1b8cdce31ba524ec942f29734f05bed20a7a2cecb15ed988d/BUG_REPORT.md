# Bug Report

## Metadata
- Skill: sub2api-summary
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 9c20a075c5fe78a1b8cdce31ba524ec942f29734f05bed20a7a2cecb15ed988d
- Severity: high
- Occurrence count: 1
- First seen at: 2026-06-28T01:43:11Z
- Last seen at: 2026-06-28T01:43:11Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
支付看板响应中的通用 user 字段未被脱敏

## Expected Behavior
只读采集脚本在落盘前应脱敏所有可能包含邮箱、用户名或账号标识的字段，包括 payment dashboard recent_orders 中的 user 字段。

## Actual Behavior
采集 payment dashboard 时，recent_orders 里的 user 字段可能保留原始邮箱形式，说明脱敏规则只覆盖了 email/username 等字段名，没有覆盖通用 user 字段。

## Reproduction Steps
- 使用 sub2api-summary 对真实站点执行只读采集。
- 检查脱敏后的 payment_dashboard.json 中 recent_orders[*].user 字段。

## Evidence
- payment_dashboard.json 的 recent_orders[*].user 字段可能出现未脱敏邮箱；未在任务输出中复述具体值。

## Environment Notes
- Skill source path: redacted
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
当前任务不引用该字段；后续分析只使用聚合收入和脱敏 top_users。

## Additional Notes
None
