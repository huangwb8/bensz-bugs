# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: dab823dbcbac00c2d8446d5168a7d7a3c959f25ab48946f989b9dd763b91713f
- Severity: high
- Occurrence count: 1
- First seen at: 2026-08-08T05:16:16Z
- Last seen at: 2026-08-08T05:16:16Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows pandoc auto-install validates executable path without exe suffix

## Expected Behavior
After downloading the Windows Pandoc zip, the renderer should detect pandoc.exe and proceed to R Markdown rendering.

## Actual Behavior
The installer checks bin/pandoc without the Windows exe suffix and exits with pandoc binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py on Windows with Pandoc absent from PATH.
- Allow automatic Pandoc installation and observe the post-extraction binary check.

## Evidence
- pandoc binary not found after installation; existing executable is pandoc.exe

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
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Prepend the existing user local bin directory containing pandoc.exe to PATH and invoke with --no-install.

## Additional Notes
None
