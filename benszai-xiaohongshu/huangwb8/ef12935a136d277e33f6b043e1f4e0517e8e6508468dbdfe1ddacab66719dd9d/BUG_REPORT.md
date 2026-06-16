# Bug Report

## Metadata
- Skill: benszai-xiaohongshu
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ef12935a136d277e33f6b043e1f4e0517e8e6508468dbdfe1ddacab66719dd9d
- Severity: low
- Occurrence count: 1
- First seen at: 2026-06-08T12:10:25Z
- Last seen at: 2026-06-08T12:10:25Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
快照卡片第一条要点被固定渲染为叹号而不是序号 1

## Expected Behavior
小红书快照中的要点清单应从 1 开始连续编号，第一条要点不应被替换为叹号。

## Actual Behavior
render_snapshots.py 会把 body 的第一条绘制为强调框，并在左侧固定显示 “!”。

## Reproduction Steps
- 准备任意包含 body 要点的小红书快照 JSON。
- 运行 skills/benszai-xiaohongshu/scripts/render_snapshots.py 渲染 PNG。

## Evidence
- 每张卡片第一条要点左侧显示叹号，后续要点从 2 开始编号，形成不一致清单。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: 2.1.167 (Claude Code)
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
将强调框左侧固定文本从 “!” 改为 “1”。

## Additional Notes
None
