# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: e5bda788840a68c2c709aae14006c6281da7ffccfd2ab8b5481a0685ce85d1b9
- Severity: high
- Occurrence count: 1
- First seen at: 2026-08-06T05:20:28Z
- Last seen at: 2026-08-06T05:20:28Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc auto-install checks a Unix-style bin/pandoc path instead of the extracted pandoc.exe

## Expected Behavior
After downloading and extracting the Windows Pandoc zip, the wrapper should locate pandoc.exe and continue rendering.

## Actual Behavior
The archive extracts successfully with pandoc.exe in the version directory, but the wrapper checks a bin/pandoc path and exits with pandoc binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py on Windows without pandoc already in PATH.
- Allow the wrapper to download and extract the supported Windows Pandoc zip.

## Evidence
- The extracted archive contains pandoc.exe, while the wrapper checks a Unix-style bin/pandoc path.

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
  - pandoc: 3.8.3
  - python: 3.13
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Prepend the extracted Pandoc version directory containing pandoc.exe to PATH and rerun with --no-install.

## Additional Notes
None
