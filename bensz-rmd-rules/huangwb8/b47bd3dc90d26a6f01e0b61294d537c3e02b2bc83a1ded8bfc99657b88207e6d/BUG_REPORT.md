# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: b47bd3dc90d26a6f01e0b61294d537c3e02b2bc83a1ded8bfc99657b88207e6d
- Severity: low
- Occurrence count: 1
- First seen at: 2026-07-14T23:50:14Z
- Last seen at: 2026-07-14T23:50:14Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows report checker fails when printing Unicode status symbols to GBK console

## Expected Behavior
The checker should exit successfully after a passing report on Windows.

## Actual Behavior
The checker reports zero failed blocks then exits with UnicodeEncodeError while printing its status symbol.

## Reproduction Steps
- Run the strict figure and table interpretation checker from a Windows GBK console.
- Use an Rmd report that passes the checker.

## Evidence
- UnicodeEncodeError: gbk codec cannot encode character U+2705 after the report shows zero failed blocks.

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
Set PYTHONIOENCODING=utf-8 for the checker process.

## Additional Notes
None
