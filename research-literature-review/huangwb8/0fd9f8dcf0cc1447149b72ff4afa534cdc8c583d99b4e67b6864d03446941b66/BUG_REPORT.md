# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0fd9f8dcf0cc1447149b72ff4afa534cdc8c583d99b4e67b6864d03446941b66
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-02T09:42:10Z
- Last seen at: 2026-08-02T09:42:10Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Pipeline runner crashes on Windows GBK console when printing a Unicode stage marker

## Expected Behavior
The Premium review pipeline should start on a standard Windows PowerShell console.

## Actual Behavior
The runner raises UnicodeEncodeError before executing the first stage.

## Reproduction Steps
- Run run_pipeline.py with a topic and Premium review level in Windows PowerShell.
- Observe failure while printing the stage header.

## Evidence
- UnicodeEncodeError: 'gbk' codec cannot encode Unicode stage marker

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
Set PYTHONUTF8=1 before launching the pipeline.

## Additional Notes
None
