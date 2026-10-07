# Bug Report

## Metadata
- Skill: auto-test-code
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: ef7619e5100736523a979fa33a06768732b5896b96e073c7d114cc2ca1407636
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-09-15T05:53:20Z
- Last seen at: 2026-09-15T05:53:20Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
create_session.py cannot target an already locked unified task workspace

## Expected Behavior
The initializer should accept a caller-supplied task workspace or honor the active unified task root.

## Actual Behavior
The CLI rejects a task-root override and can only derive the legacy fixed workspace from code-root.

## Reproduction Steps
- Start a task with a locked .bensz-api/task-* root.
- Run create_session.py with a task-root override.

## Evidence
- argparse rejects --tmp-root as an unrecognized argument.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: OpenAI Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.154.0-alpha.6.1
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Create the documented A/B session skeleton manually inside the locked task root.

## Additional Notes
None
