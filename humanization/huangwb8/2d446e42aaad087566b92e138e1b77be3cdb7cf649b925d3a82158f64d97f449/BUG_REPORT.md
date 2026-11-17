# Bug Report

## Metadata
- Skill: humanization
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 2d446e42aaad087566b92e138e1b77be3cdb7cf649b925d3a82158f64d97f449
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-11-17T06:01:46Z
- Last seen at: 2026-11-17T06:01:46Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows managed runtime is rejected by hard-coded POSIX Python and BSK paths

## Expected Behavior
The control entry accepts the installer-managed native Windows python.exe and bsk.cmd.

## Actual Behavior
init returns managed_python_required although installer runtime health is ready and BSK is 2.1.6.

## Reproduction Steps
- Prepare the managed runtime with bootstrap_install.py --ensure-runtime on Windows.
- Invoke installed humanization/scripts/control.py init using that managed python.exe.

## Evidence
- control.py lines 24-25 hard-code bin/python and extensionless bin/bsk; line 44 rejects native Windows executable paths.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.169.0-alpha.11.1
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Preserve drafts and review evidence; do not patch installed skill source or fabricate ready.

## Additional Notes
None
