# Bug Report

## Metadata
- Skill: paper-explain-figures
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: bed40e9ac417c561ff1ab635b97c5ebbc9872a8f4a6f5598b0cd9d97c279f80c
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-09-10T07:52:24Z
- Last seen at: 2026-09-10T07:52:24Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Runner cannot reuse a host-locked task workspace

## Expected Behavior
The runner should accept and reuse the task root already declared and locked by the host workflow.

## Actual Behavior
The runner always constructs a new timestamped task root under the current working directory, so invoking it after the host locks a root creates a second task root.

## Reproduction Steps
- Declare a unique task root for a figure interpretation task.
- Run paper_explain_figures.py from the project root and inspect lines 1184-1206 or the created directory.

## Evidence
- The script assigns task_root from cwd plus a fresh datetime stamp and has no task-root override.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.153.4
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Run a temporary compatibility copy inside the already locked task workspace and redirect all generated files there.

## Additional Notes
None
