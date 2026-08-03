# Bug Report

## Metadata
- Skill: sub2api-reimbursement
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 27f8b60dadba0b7ee12b5b5ce5c2c99dd6e6723921f57693465e4987867600ac
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-17T03:15:51Z
- Last seen at: 2026-07-17T03:15:51Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
detail-only 上传说明承诺自动设为可见，但脚本实际需要额外 sync-record 参数

## Expected Behavior
仅上传明细时应自动将复用记录同步为可见，使后台能够发送附件通知。

## Actual Behavior
上传脚本只有传入 sync-record 才更新记录；默认 detail-only 后记录仍可能不可见。

## Reproduction Steps
- 对不可见的既有发票记录运行上传脚本并传入 detail-only。
- 检查脚本条件分支，未提供 sync-record 时不会调用更新接口。

## Evidence
- 技能说明宣称 detail-only 会同步记录为用户可见，而脚本实现仅在 sync-record 参数为真时更新。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
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
detail-only 模式自动同步复用记录，并加入针对该行为的单元测试。

## Additional Notes
None
