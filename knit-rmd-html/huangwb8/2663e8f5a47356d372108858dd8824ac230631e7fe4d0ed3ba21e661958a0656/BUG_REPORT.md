# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 2663e8f5a47356d372108858dd8824ac230631e7fe4d0ed3ba21e661958a0656
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-01T09:25:59Z
- Last seen at: 2026-08-01T09:25:59Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc bootstrap installs binary into a nested directory but fails post-install discovery

## Expected Behavior
After automatically installing Pandoc, the wrapper should discover the installed executable and continue rendering.

## Actual Behavior
The wrapper stopped with pandoc binary not found after installation although the Pandoc executable existed in the downloaded nested version directory.

## Reproduction Steps
- Run knit_rmd_html.py on Windows with Rscript available but Pandoc absent from PATH.
- Allow the wrapper to auto-install its default Pandoc version.

## Evidence
- Wrapper exits with pandoc binary not found after installation; directly invoking the nested pandoc executable reports the expected version and rendering succeeds when that directory is prepended to PATH.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
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
Prepend the actual nested Pandoc directory to PATH, set RSTUDIO_PANDOC to that directory, and rerun the wrapper with --no-install.

## Additional Notes
None
