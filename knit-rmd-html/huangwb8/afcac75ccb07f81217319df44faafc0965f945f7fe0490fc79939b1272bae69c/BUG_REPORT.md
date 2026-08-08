# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: afcac75ccb07f81217319df44faafc0965f945f7fe0490fc79939b1272bae69c
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-12T11:20:14Z
- Last seen at: 2026-07-12T11:20:14Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows Pandoc 3.8.3 ZIP layout is incompatible with installer path assumption

## Expected Behavior
Auto-install should locate pandoc.exe from the official Windows ZIP and continue rendering.

## Actual Behavior
The ZIP extracts pandoc.exe directly under the version folder, but the installer requires bin/pandoc and exits with binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py for an Rmd when pandoc is absent from PATH on Windows.
- Observe successful archive download followed by pandoc binary not found after installation.

## Evidence
- Official Windows archive extracted pandoc.exe at pandoc-3.8.3/pandoc.exe, while _install_pandoc_zip returns pandoc-3.8.3/bin/pandoc.

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
Prepend the actual extracted pandoc.exe directory to PATH and rerun the wrapper with --no-install.

## Additional Notes
None
