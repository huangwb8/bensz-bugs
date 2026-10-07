# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: db0ff60ce7f59876ab6fab8e535331cc9404caa548efe86e3d7438e2914bdff8
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-09T06:03:41Z
- Last seen at: 2026-08-09T06:03:41Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Rmd 解读质量检查将 LaTeX 公式常数误判为未追踪结果数字

## Expected Behavior
数字可追溯检查应忽略数学定义公式中的指数和常数，只检查解释性正文中的结果数字。

## Actual Behavior
包含标准 LaTeX 公式时，默认与严格质量检查把公式中的数字计为未追踪字面数字并导致门禁失败。

## Reproduction Steps
- 在 Rmd 正文加入含平方指数或固定分母的 LaTeX 公式。
- 运行 check_interpretation_quality.py 目标Rmd。

## Evidence
- 报告 untracked literal numbers，并将 LaTeX 公式行列为示例。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.144.0-alpha.4
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
保留公式并将该项作为启发式误报记录；继续运行覆盖检查、htmlwidget 检查、渲染和人工数字溯源。

## Additional Notes
None
