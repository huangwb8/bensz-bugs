# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: a378992d0726afca609e310158c1cc64e387acb4e4d7906ff96eca782ea8c5b6
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-16T07:47:33Z
- Last seen at: 2026-07-16T07:47:33Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Pandoc Windows zip layout is incompatible with installer path assumption

## Expected Behavior
The wrapper should install and detect the requested Pandoc release on Windows.

## Actual Behavior
The release extracts pandoc.exe at the package root, while the installer expects bin/pandoc, so it reports pandoc binary not found after installation.

## Reproduction Steps
- Run knit_rmd_html.py on Windows when pandoc is not initially present in PATH.

## Evidence
- pandoc binary not found after installation; extracted archive contains pandoc.exe at its root.

## Environment Notes
- Skill source path: None
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
Prepend the existing local Pandoc directory to PATH and run with --no-install.

## Additional Notes
None
