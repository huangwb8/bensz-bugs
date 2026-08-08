# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0ce03299a2a6361dfe2477f696e55bf40478c316346fd4e0536efa669bd53bd3
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-16T07:43:49Z
- Last seen at: 2026-07-16T07:43:49Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows GBK console crashes when interpretation checker prints Unicode status symbol

## Expected Behavior
The checker should report pass or fail and exit with its intended status on a default Windows console.

## Actual Behavior
After reporting failed blocks, printing the Unicode cross mark raises UnicodeEncodeError under GBK and masks the intended checker exit.

## Reproduction Steps
- Run check_figure_table_interpretation.py with --strict on a report that fails coverage checks in a default Windows PowerShell environment.

## Evidence
- UnicodeEncodeError: 'gbk' codec cannot encode character U+274C

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows
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
Set PYTHONUTF8=1 before running the checker.

## Additional Notes
None
