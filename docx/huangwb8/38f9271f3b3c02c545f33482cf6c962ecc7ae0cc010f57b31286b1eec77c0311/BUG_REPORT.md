# Bug Report

## Metadata
- Skill: docx
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 38f9271f3b3c02c545f33482cf6c962ecc7ae0cc010f57b31286b1eec77c0311
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-08T09:14:51Z
- Last seen at: 2026-08-08T09:14:51Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
soffice wrapper assumes TemporaryDirectory supports ignore_cleanup_errors

## Expected Behavior
The bundled soffice wrapper should launch LibreOffice conversion on supported Python 3 runtimes.

## Actual Behavior
The wrapper exits before invoking LibreOffice because TemporaryDirectory rejects the ignore_cleanup_errors keyword.

## Reproduction Steps
- Run the bundled docx scripts/office/soffice.py with --help or a headless conversion command under Python 3.9.

## Evidence
- TypeError: __init__() got an unexpected keyword argument 'ignore_cleanup_errors'

## Environment Notes
- Skill source path: redacted
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
Invoke the installed LibreOffice executable directly with a temporary user profile and headless conversion arguments.

## Additional Notes
None
