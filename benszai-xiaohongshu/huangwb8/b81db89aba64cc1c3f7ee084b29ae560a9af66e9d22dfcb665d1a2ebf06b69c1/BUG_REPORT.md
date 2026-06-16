# Bug Report

## Metadata
- Skill: benszai-xiaohongshu
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: b81db89aba64cc1c3f7ee084b29ae560a9af66e9d22dfcb665d1a2ebf06b69c1
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-05-28T14:46:19Z
- Last seen at: 2026-05-28T14:46:19Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
小红书快照正文要点使用叉号装饰导致被误解为错误项

## Expected Behavior
快照正文要点的装饰符号应保持中性或明确表达层级，不应让正确要点被误读为错误、禁忌或不推荐。

## Actual Behavior
render_snapshots.py 在部分要点右侧绘制叉号装饰，用户反馈含义不明，容易误解为该条内容是错误项。

## Reproduction Steps
- 使用 benszai-xiaohongshu 生成包含多个正文要点的 bold 主题快照。
- 查看生成卡片中第 3、5 等要点右侧的叉号装饰。

## Evidence
- 用户反馈：有一些叉，含义不明；这是错误？还是啥？但明明好像是对的。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: desktop
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.119 (Claude Code)
  - codex: codex-cli 0.124.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
将叉号装饰替换为中性的右侧强调短线/圆点后重新渲染快照。

## Additional Notes
None
