# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0efa3d9d11012c7eb05bec626ab0425615aabe18df40b98757003c9badd1da03
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-08T13:19:45Z
- Last seen at: 2026-08-08T13:19:45Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows GBK console output crashes init-project when status messages contain Unicode checkmarks.

## Expected Behavior
The auto initializer completes or emits console output compatible with the active Windows console encoding.

## Actual Behavior
The script exits before initialization with UnicodeEncodeError while printing a checkmark to a GBK console.

## Reproduction Steps
- Run the initializer with --auto in a Windows PowerShell session using GBK console output.
- Ensure the bac dependency is already installed so the script prints its dependency-status message.

## Evidence
- UnicodeEncodeError: gbk codec cannot encode character U+2705 while printing the bac dependency status.

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
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Set PYTHONIOENCODING=utf-8 for the initializer process.

## Additional Notes
None
