# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 155538fac85dd62e77697c91fcc88d5a311a2ac3dce47d4e07c5db66d76893ac
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-22T01:11:26Z
- Last seen at: 2026-07-22T01:11:26Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows pandoc zip layout is incompatible with the bootstrap path assumption

## Expected Behavior
After downloading and extracting the Windows pandoc archive, the wrapper should locate pandoc.exe and continue rendering.

## Actual Behavior
Pandoc is extracted successfully, but the wrapper searches for a bin subdirectory and reports that the binary was not found.

## Reproduction Steps
- Run knit_rmd_html.py on Windows when pandoc is absent from PATH.
- Allow the wrapper to download and extract pandoc 3.8.3.

## Evidence
- Extracted binary exists under pandoc-version/pandoc-version/pandoc.exe, while the wrapper expects pandoc-version/bin/pandoc.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: OpenAI Codex
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
Add the actual extracted pandoc directory to PATH and rerun with --no-install.

## Additional Notes
None
