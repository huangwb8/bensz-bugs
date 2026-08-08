# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: bdfb38e55ec798ec94c2a1a0cf474aae59d473726a170af93ee49c4fb2c8e35b
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-06T21:08:24Z
- Last seen at: 2026-08-06T21:08:24Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc bootstrap cannot discover executable extracted into a duplicated version directory

## Expected Behavior
After downloading and extracting Pandoc, the wrapper should locate the executable and continue rendering.

## Actual Behavior
Pandoc is extracted successfully under two nested version directories, but the wrapper reports that the binary is not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py for an Rmd on Windows without pandoc already on PATH.
- Observe the binary under a duplicated version directory and the wrapper failure.

## Evidence
- Wrapper reports pandoc binary not found after installation while pandoc.exe exists under pandoc-version/pandoc-version.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex CLI
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
Prepend the actual nested Pandoc executable directory to PATH before invoking the wrapper.

## Additional Notes
None
