# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 86e71e42fb777d20131031a08458be47993a9b5fb9a0cf2dbaf5a188b7e37f5a
- Severity: minor
- Occurrence count: 1
- First seen at: 2026-07-21T12:43:49Z
- Last seen at: 2026-07-21T12:43:49Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows GBK 控制台下检查器输出 Unicode 勾号导致异常退出

## Expected Behavior
图表解读检查完成后应正常返回检查结果。

## Actual Behavior
检查已判定 6 个可见输出且 0 个未通过，但结尾 print Unicode 勾号时抛出 UnicodeEncodeError。

## Reproduction Steps
- 在 Windows 默认 GBK 控制台运行 check_figure_table_interpretation.py。
- 对包含可见图表输出的 Rmd 使用 --strict。

## Evidence
- Traceback 位于 print Unicode 勾号，错误为 gbk codec cannot encode character U+2705。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: codex
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
设置 PYTHONIOENCODING=utf-8 后运行检查器。

## Additional Notes
None
