# Bug Report

## Metadata
- Skill: bensz-auto-contribution
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 5d53aa20b4d4392d79e0346fa35130a99b5a051c33ad9bd830057aa3a16f61d4
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-23T11:27:55Z
- Last seen at: 2026-07-23T11:27:55Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
BAC root identity becomes invalid when a Git remote is added after ledger initialization

## Expected Behavior
A valid ledger should remain appendable after normal repository initialization or should provide a supported project-identity migration.

## Actual Behavior
BAC 1.3.2 includes git_remote in project.root_hash; adding a remote changes the hash, verify fails, append is refused, and stale-tail repair refuses the case.

## Reproduction Steps
- Initialize and record a BAC ledger before the repository has a Git remote.
- Add a Git remote, then record another BAC event.
- Run bac verify and bac repair stale-tail.

## Evidence
- verify reports project.root_hash changed within ledger; the root path is unchanged while git_remote changes from null to a URL; stale-tail repair reports no eligible mismatch.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: OpenAI Codex
- Key software versions:
  - bac: 1.3.2
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
Recover the invalid uncommitted tail from a verified snapshot, then invoke BAC with a process-local Git configuration override that preserves the original null remote identity. Do not change repository configuration.

## Additional Notes
None
