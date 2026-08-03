# Bug Report

## Metadata
- Skill: xlsx
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: d779e61e0586cb44243aae900d8d342174009582cb545a01331ae9d3fbe08001
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-24T16:42:46Z
- Last seen at: 2026-07-24T16:42:46Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
recalc.py uses TemporaryDirectory ignore_cleanup_errors without enforcing Python 3.10+

## Expected Behavior
The recalculation helper should run on the advertised environment or detect Python version and provide a compatible fallback.

## Actual Behavior
On Python 3.9 the helper raises TypeError before opening the workbook.

## Reproduction Steps
- Invoke recalc.py with Python 3.9 on a valid xlsx file.

## Evidence
- TypeError: __init__() got an unexpected keyword argument 'ignore_cleanup_errors'

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python3: Python 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Run the unchanged helper with Python 3.12.

## Additional Notes
None
