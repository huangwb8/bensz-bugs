# Bug Report

## Metadata
- Skill: benszai-xiaohongshu
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 3cab1119c32136d70b649edce15c5f5d1eea8babb22406bb0c90d2dfb4630bcc
- Severity: low
- Occurrence count: 1
- First seen at: 2026-06-08T12:03:17Z
- Last seen at: 2026-06-08T12:03:17Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
快照渲染脚本会自动添加无意义的要点数量备注

## Expected Behavior
小红书快照应只展示用户文案或 JSON 规格中的内容，不应自动添加无关提示语。

## Actual Behavior
当卡片 body 超过 5 个要点时，render_snapshots.py 会在图片底部绘制“共 N 个要点，建议收藏慢慢看”。

## Reproduction Steps
- 准备一个 body 超过 5 条的小红书快照 JSON。
- 运行 skills/benszai-xiaohongshu/scripts/render_snapshots.py 渲染 PNG。

## Evidence
- 图片中出现未在用户文案或 JSON 中定义的“共6个要点，建议收藏慢慢看”。

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
删除 render_snapshots.py 中自动绘制该备注的逻辑，然后重新渲染。

## Additional Notes
None
