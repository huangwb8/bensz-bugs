# Bug Report

## Metadata
- Skill: paper-explain-figures
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 1d5ac6f17d837cb5c7bb8f3bdebc266d644c938664a3767753b03b5b4fab5e5b
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-24T16:42:45Z
- Last seen at: 2026-07-24T16:42:45Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Integrity check treats an automatically modified existing .DS_Store as an unauthorized path change

## Expected Behavior
The runner should ignore operating-system metadata changes or compare only task-owned paths while preserving user files.

## Actual Behavior
A successful local-runner pass was rejected because an existing .DS_Store changed during execution.

## Reproduction Steps
- Run the skill from a macOS project directory containing an existing .DS_Store.
- Allow Finder or the filesystem to update that file while the skill is running.

## Evidence
- [ERROR] detected a modified unauthorized path: .DS_Store

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
Run the skill from a clean isolated directory inside the declared task workspace.

## Additional Notes
None
