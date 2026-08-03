# Bug Report

## Metadata
- Skill: bac-contribution-ledger
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 4f06bb4e9d460c96dbe179501759445ed8b3c16893bb8c38b9f663db557c6e77
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-11T09:01:22Z
- Last seen at: 2026-07-11T09:01:22Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
BAC ledger cannot append after repository identity changes from uninitialized to Git-managed

## Expected Behavior
A valid existing ledger should support a new contribution event after the project initializes Git, or provide a supported root identity migration command.

## Actual Behavior
The first new event is appended with a different project root hash, immediately making the ledger invalid; later appends fail and stale-tail repair refuses because prev_event_hash is valid.

## Reproduction Steps
- Initialize a BAC ledger before Git metadata exists.
- Initialize Git or otherwise establish repository identity, then append one BAC record.
- Run bac verify and observe project.root_hash changed within ledger.

## Evidence
- bac verify reports project.root_hash changed within ledger; bac repair stale-tail refuses because there is no prev_event_hash mismatch.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Back up the ledger, remove only the newly appended invalid tail event from the container, verify the original ledger, and omit new records until root identity migration is supported.

## Additional Notes
None
