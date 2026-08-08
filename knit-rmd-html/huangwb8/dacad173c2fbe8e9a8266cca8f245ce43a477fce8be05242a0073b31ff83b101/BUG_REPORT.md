# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: dacad173c2fbe8e9a8266cca8f245ce43a477fce8be05242a0073b31ff83b101
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T16:48:09Z
- Last seen at: 2026-08-01T16:48:09Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc bootstrap extracts an extra nested version directory and then fails discovery

## Expected Behavior
After downloading and extracting Pandoc, the wrapper should discover pandoc.exe and continue rendering.

## Actual Behavior
The archive extracts to a nested pandoc-version directory while discovery checks the parent layout, so the wrapper exits with pandoc binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py for an Rmd on Windows with no Pandoc on PATH.
- Inspect the bootstrap directory and observe pandoc.exe one version directory deeper than the path used for discovery.

## Evidence
- Wrapper error: pandoc binary not found after installation; executable exists under nested version/version/pandoc.exe.

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
Prepend the actual nested executable directory to PATH and set RSTUDIO_PANDOC before rerunning with no install.

## Additional Notes
None
