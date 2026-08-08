# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 03ffc551fed943d4fb54ae4b89b1e5ce47955559218fc1f07860a188698a75f0
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-21T12:53:30Z
- Last seen at: 2026-07-21T12:53:30Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows wrapper cannot locate an installed Pandoc executable after bootstrap

## Expected Behavior
The Windows renderer should detect or install Pandoc and invoke rmarkdown::render.

## Actual Behavior
The wrapper stops with pandoc binary not found after installation before rendering.

## Reproduction Steps
- Run the knit_rmd_html.py wrapper on Windows with a valid Rmd file.
- Ensure Rscript is available and invoke the wrapper.

## Evidence
- [pandoc] pandoc binary not found after installation.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: Windows
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
Invoke rmarkdown::render directly through an available Rscript executable.

## Additional Notes
None
