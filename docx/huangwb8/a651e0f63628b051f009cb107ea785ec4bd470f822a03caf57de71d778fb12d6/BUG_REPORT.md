# Bug Report

## Metadata
- Skill: docx
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: a651e0f63628b051f009cb107ea785ec4bd470f822a03caf57de71d778fb12d6
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-07T12:48:52Z
- Last seen at: 2026-08-07T12:48:52Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
soffice.py uses TemporaryDirectory ignore_cleanup_errors unsupported on Python 3.9

## Expected Behavior
The bundled LibreOffice wrapper should render a DOCX for visual verification on the supported runtime.

## Actual Behavior
The wrapper exits before launching LibreOffice because Python 3.9 TemporaryDirectory rejects ignore_cleanup_errors.

## Reproduction Steps
- Run the bundled soffice.py wrapper with Python 3.9 and --headless --convert-to pdf.

## Evidence
- TypeError: __init__() got an unexpected keyword argument 'ignore_cleanup_errors'

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python: 3.9.6
  - python3: Python 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Invoke the system soffice binary directly with an isolated user profile.

## Additional Notes
None
