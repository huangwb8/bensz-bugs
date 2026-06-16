# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 7fcf01e002c13872c78333c4b41682644010361b2a0fa48c4c83cf21e021aec1
- Severity: low
- Occurrence count: 1
- First seen at: 2026-05-20T07:12:35Z
- Last seen at: 2026-05-20T07:12:35Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
auto-draw-plot evaluation.json 与 result.json 的 passed 判定口径不一致

## Expected Behavior
每轮 evaluation.json 应保存经过模式阈值归一化后的 passed 值，且与 meta/result.json 的 stop_reason 和 best_score 判定一致。

## Actual Behavior
schematic 测试中 evaluation.json 显示 score=8.0 且 passed=true，但 schematic 模式阈值为 8.6，meta/result.json 显示 stop_reason=max_rounds，说明最终未 accepted。

## Reproduction Steps
- 使用 schematic 模式运行一轮生成，模式阈值 accept_score=8.6。
- 查看 rounds/round-01/evaluation.json 与 meta/result.json。

## Evidence
- evaluation.json: score=8.0, passed=true；result.json: best_score=8.0, stop_reason=max_rounds, mode.accept_score=8.6。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
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
读取最终是否通过时优先以 meta/result.json 为准；修复时在 run_draw_plot.py 更新 evaluation passed 后重新写回 evaluation.json。

## Additional Notes
None
