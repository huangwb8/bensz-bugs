# Bug Report

## Metadata
- Skill: sub2api-reimbursement
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: fb9e0d03cff292d1e128ac877416d47b8af2ed83c2f23874e3f7aceff93455be
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-15T10:31:21Z
- Last seen at: 2026-07-15T10:31:21Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
按发票申请生成明细时未优先锚定既有发票记录绑定订单

## Expected Behavior
传入开票申请 ID 且后台已有发票记录时，应优先使用该记录绑定订单生成明细，金额应与发票记录一致。

## Actual Behavior
未显式传订单 ID 时，脚本从用户消费历史中选中了另一笔较新的订阅升级订单，导致明细金额与目标发票记录不一致。

## Reproduction Steps
- 为一个已完成且已有发票记录的申请运行生成脚本，只传用户 ID 和开票申请 ID。
- 比较生成摘要中的 reimbursable_orders 与既有发票记录的 orders。

## Evidence
- 目标记录绑定一笔普通订阅订单，但脚本选择了另一笔后续升级订单；显式传入目标订单 ID 后金额恢复一致。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
先读取申请对应发票记录的订单列表，再用 --order-id 或 --order-ids 显式锚定后重新生成。

## Additional Notes
None
