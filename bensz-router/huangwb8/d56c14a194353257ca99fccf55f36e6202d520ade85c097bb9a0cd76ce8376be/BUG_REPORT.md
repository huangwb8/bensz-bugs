# Bug Report

## Metadata
- Skill: bensz-router
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: d56c14a194353257ca99fccf55f36e6202d520ade85c097bb9a0cd76ce8376be
- Severity: important
- Occurrence count: 1
- First seen at: 2026-10-07T10:11:13Z
- Last seen at: 2026-10-07T10:11:13Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows hooks install creates definitions that hooks doctor rejects

## Expected Behavior
A clean user-scope MCP hooks installation should pass ownership validation and doctor.

## Actual Behavior
After successful installation, hooks doctor exits with invalid managed hook definitions.

## Reproduction Steps
- On Windows, install version 1.1.4 into a dedicated Python environment whose absolute executable path has no spaces.
- Run hooks install --harness codex --scope user --transport mcp, then hooks doctor with the same options.

## Evidence
- hook_config.py _desired uses subprocess.list2cmdline, while _is_adapter_group uses POSIX shlex.split. Unquoted Windows backslashes are removed; generated=False, quoted=True, forward-slash=True in the minimal validation test.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - bensz-router: 1.1.4
  - claude: unavailable
  - codex: codex-cli 0.162.0-alpha.2
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Quote the executable path in the five generated hook commands and matching ownership definitions; retain all matchers and context budgets. Doctor then reports setup_complete=true, no conflicts, MCP process_verified=true and tools_verified=true. Reinstalling hooks may regenerate invalid unquoted commands.

## Additional Notes
None
