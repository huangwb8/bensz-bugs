# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: da4db102da34aca1dd593240d287389b9aace8821709437052effe116711ac03
- Severity: low
- Occurrence count: 1
- First seen at: 2026-07-22T17:12:20Z
- Last seen at: 2026-07-22T17:12:20Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
图表解读覆盖脚本在 Windows GBK 终端打印 Unicode 状态符时异常退出

## Expected Behavior
检测到零个未通过块时应正常返回通过状态

## Actual Behavior
报告显示未通过块数为零，但打印 Unicode 勾号触发 UnicodeEncodeError 并返回非零状态

## Reproduction Steps
- 在 Windows GBK PowerShell 运行 check_figure_table_interpretation.py Rmd --strict

## Evidence
- 检测到输出块 6、未通过 0，随后 gbk 无法编码 U+2705

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
  - gh: unavailable
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
以报告计数作为覆盖结论，并由主代理人工复核；脚本输出阶段设置 UTF-8 或避免 Unicode 状态符

## Additional Notes
None
