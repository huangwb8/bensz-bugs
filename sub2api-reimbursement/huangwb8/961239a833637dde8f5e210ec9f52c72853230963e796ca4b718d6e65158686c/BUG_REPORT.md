# Bug Report

## Metadata
- Skill: sub2api-reimbursement
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 961239a833637dde8f5e210ec9f52c72853230963e796ca4b718d6e65158686c
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-15T10:31:21Z
- Last seen at: 2026-07-15T10:31:21Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
detail-only 文档声称自动设为可见但上传脚本未同步记录可见性

## Expected Behavior
使用 --detail-only 复用既有记录后，应按技能文档将记录同步为用户可见，并触发附件通知。

## Actual Behavior
脚本只上传了明细附件，既有记录仍保持 visible=false，通知时间为空；只有另行更新记录可见性后通知流程才触发。

## Reproduction Steps
- 对一个 visible=false 且无附件的既有发票记录运行上传脚本，并指定 --detail-only。
- 上传后通过只读接口回查记录的 visible 与 notification_sent_at。

## Evidence
- 附件创建成功但记录仍不可见且无通知时间，与技能文档描述不一致。

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
上传后显式同步记录为 visible=true，并回查 notification_sent_at；后续应让脚本在上传前安全同步可见性。

## Additional Notes
None
