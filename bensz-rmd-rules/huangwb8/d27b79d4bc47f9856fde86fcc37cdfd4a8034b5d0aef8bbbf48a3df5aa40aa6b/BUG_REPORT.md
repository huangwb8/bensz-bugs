# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: d27b79d4bc47f9856fde86fcc37cdfd4a8034b5d0aef8bbbf48a3df5aa40aa6b
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-06T05:12:51Z
- Last seen at: 2026-08-06T05:12:51Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Static interpretation checker crashes when printing status glyphs on a Windows GBK console

## Expected Behavior
The checker should finish with a pass or fail exit code and print its report on supported Windows consoles.

## Actual Behavior
After producing the diagnostic report, Python raises UnicodeEncodeError while printing a checkmark or cross glyph through the GBK console encoding.

## Reproduction Steps
- Run check_figure_table_interpretation.py with --strict in a Windows PowerShell session whose stdout encoding is GBK.
- Observe the report followed by UnicodeEncodeError for a Unicode status glyph.

## Evidence
- UnicodeEncodeError: 'gbk' codec cannot encode the status glyph

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
  - python: 3.13
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)
  - shell: Windows PowerShell

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Set PYTHONUTF8=1 for the checker process so stdout uses UTF-8.

## Additional Notes
None
