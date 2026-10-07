# Bug Report

## Metadata
- Skill: install-bensz-skills
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 5115bb8c13c74c7763cd12ad760c0ef29a52326114f36e1c8bc3fd40cb2201d6
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-09-17T13:58:07Z
- Last seen at: 2026-09-17T13:58:07Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows remote install emits a subprocess reader UnicodeDecodeError while the main installation continues

## Expected Behavior
Remote installation should decode Git subprocess output without background thread exceptions on Windows.

## Actual Behavior
A subprocess reader thread raised UnicodeDecodeError using the GBK codec, while the installer returned zero and completed both target installations.

## Reproduction Steps
- On Windows PowerShell with Python 3.12, run install.py --remote --auto --general.
- Observe a background reader thread UnicodeDecodeError before the normal installation report.

## Evidence
- UnicodeDecodeError: 'gbk' codec can't decode a byte from Git subprocess output.

## Environment Notes
- Skill source path: None
- Skill source repo: https://github.com/huangwb8/skills
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex CLI on Windows PowerShell
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.154.0-alpha.6.1
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python: 3.12.2
  - python3: unavailable
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Treat the console exception as non-fatal only after validating exit code and generated manifests.

## Additional Notes
None
