# Bug Report

## Metadata
- Skill: docx
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: b108a67e84ab1df99e29834c5b5bd7fa22791d0e743d881ab7eebee526a4587d
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-08T09:18:12Z
- Last seen at: 2026-08-08T09:18:12Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
docx OOXML validator requires Python 3.10 syntax without a runtime guard

## Expected Behavior
The bundled OOXML validator should either run on the active supported Python runtime or fail early with a clear version requirement.

## Actual Behavior
The validator exits at parse time under Python 3.9 because it uses the Python 3.10 match statement.

## Reproduction Steps
- Run docx scripts/office/validate.py under Python 3.9 against a valid docx file.

## Evidence
- SyntaxError at match family:

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
Use ZIP integrity, xmllint, Pandoc readback, and LibreOffice rendering as independent validation checks.

## Additional Notes
None
