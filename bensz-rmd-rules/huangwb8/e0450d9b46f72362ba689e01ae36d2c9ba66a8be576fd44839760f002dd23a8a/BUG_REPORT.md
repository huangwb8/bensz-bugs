# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: e0450d9b46f72362ba689e01ae36d2c9ba66a8be576fd44839760f002dd23a8a
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-22T01:06:35Z
- Last seen at: 2026-07-22T01:06:35Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows GBK console crashes after successful figure interpretation check

## Expected Behavior
The checker should print its final pass status and return success on a valid Rmd regardless of the Windows console encoding.

## Actual Behavior
The checker reports zero failed blocks, then raises UnicodeEncodeError while printing the check-mark symbol and exits with code 1.

## Reproduction Steps
- Run check_figure_table_interpretation.py on a valid Rmd with --strict in a Windows PowerShell session using the default GBK stdout encoding.
- Observe that the semantic check completes, but final status output fails.

## Evidence
- UnicodeEncodeError: 'gbk' codec cannot encode character U+2705; detected output blocks: 6; failed blocks: 0.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: OpenAI Codex
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
Set PYTHONIOENCODING=utf-8 before invoking the checker.

## Additional Notes
None
