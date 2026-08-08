# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: b579e0f6826ba9b2f8ee3f02af5c1179a506890e9e95a3331aa6bd3c9cc492d0
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-08T11:48:41Z
- Last seen at: 2026-08-08T11:48:41Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc ZIP layout is detected with a POSIX-only bin path

## Expected Behavior
After downloading the official Windows Pandoc ZIP, locate pandoc.exe and continue rendering.

## Actual Behavior
The archive is downloaded and extracted, but the wrapper searches a nonexistent bin/pandoc path and exits with binary not found.

## Reproduction Steps
- On Windows with pandoc absent from PATH, invoke knit_rmd_html.py for any valid Rmd.
- Observe that the official ZIP extracts pandoc.exe at the archive folder root while the wrapper checks a bin subdirectory.

## Evidence
- The extracted archive contains pandoc.exe at its version directory root; the wrapper reports pandoc binary not found after installation.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: Windows workstation
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
Prepend the extracted Windows Pandoc directory containing pandoc.exe to PATH and invoke the wrapper with --no-install.

## Additional Notes
None
