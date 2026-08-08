# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 3a96df2231263ae6878e990d791196e1535bd941dbc9048ab3ffc0f47c1be00b
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T15:12:11Z
- Last seen at: 2026-08-01T15:12:11Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Static checkers crash when Windows stdout uses a non-UTF-8 code page

## Expected Behavior
The checker should print pass or failure details and return its semantic exit code on supported Windows terminals.

## Actual Behavior
Printing check marks, cross marks, or a Unicode minus sign raises UnicodeEncodeError under a GBK stdout encoding and replaces the semantic result with a traceback.

## Reproduction Steps
- Run check_figure_table_interpretation.py on an Rmd file from a Windows PowerShell session using the default legacy code page.
- Observe UnicodeEncodeError while the checker prints its final status or an interpretation preview.

## Evidence
- UnicodeEncodeError: gbk codec cannot encode check-mark or minus-sign characters.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows workstation
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
Set PYTHONIOENCODING=utf-8 for checker processes and inspect the semantic report before any traceback.

## Additional Notes
None
