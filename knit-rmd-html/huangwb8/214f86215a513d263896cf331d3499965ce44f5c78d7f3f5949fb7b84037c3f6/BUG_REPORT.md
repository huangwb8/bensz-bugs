# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 214f86215a513d263896cf331d3499965ce44f5c78d7f3f5949fb7b84037c3f6
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-22T06:37:37Z
- Last seen at: 2026-07-22T06:37:37Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc auto-install assumes a nonexistent bin subdirectory

## Expected Behavior
The wrapper should locate pandoc.exe from the official Windows zip and render the Rmd after auto-installation.

## Actual Behavior
The official Pandoc Windows zip extracts pandoc.exe at the package root, but the wrapper checks a bin/pandoc path and exits with pandoc binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py on Windows without pandoc in PATH and allow the default Pandoc 3.8.3 auto-install.
- Observe that the archive is extracted but the wrapper exits before rendering because it looks for bin/pandoc.

## Evidence
- Downloaded archive contains pandoc.exe at the extracted package root while the wrapper constructs a bin/pandoc path.

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
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Add the extracted package root containing pandoc.exe to PATH and rerun the wrapper with --no-install.

## Additional Notes
None
