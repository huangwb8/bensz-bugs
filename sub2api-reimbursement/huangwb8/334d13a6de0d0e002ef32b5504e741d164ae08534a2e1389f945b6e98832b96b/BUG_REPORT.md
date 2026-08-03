# Bug Report

## Metadata
- Skill: sub2api-reimbursement
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 334d13a6de0d0e002ef32b5504e741d164ae08534a2e1389f945b6e98832b96b
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-17T03:11:07Z
- Last seen at: 2026-07-17T03:11:07Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
复杂02 明细把技术解释固定写入备注，无法满足仅保留配套使用说明的开票场景

## Expected Behavior
默认正式明细仅保留必要的配套使用说明；技术估算和服务抽象的解释应仅在需要时出现。

## Actual Behavior
复杂02 模板固定渲染第 2、3 条技术解释，生成脚本没有控制开关。

## Reproduction Steps
- 使用默认复杂02模板生成一份订阅费用明细。
- 检查备注区域，可复现固定的第 2、3 条技术解释。

## Evidence
- 已生成的正式明细包含三条备注，其中第 2、3 条不属于所有开票场景所需内容。

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
修改模板，使默认输出仅保留第一条必要说明，并增加回归测试。

## Additional Notes
None
