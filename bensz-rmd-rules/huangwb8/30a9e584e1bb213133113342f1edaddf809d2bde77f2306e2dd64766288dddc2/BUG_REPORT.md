# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 30a9e584e1bb213133113342f1edaddf809d2bde77f2306e2dd64766288dddc2
- Severity: important
- Occurrence count: 1
- First seen at: 2026-09-15T09:14:23Z
- Last seen at: 2026-09-15T09:14:23Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
00.Environment.R template opens the default PDF device during source and creates Rplots.pdf

## Expected Behavior
Sourcing the environment template should configure plot defaults without creating files or opening a graphics device.

## Actual Behavior
The template calls graphics::par() unconditionally; in a non-interactive R session this opens the default PDF device and leaves an empty Rplots.pdf in the working directory.

## Reproduction Steps
- Start a non-interactive R session in an empty working directory.
- Source a 00.Environment.R generated from the bensz-rmd-rules template.
- Observe that Rplots.pdf is created even though no plot was requested.

## Evidence
- The installed template calls graphics::par(family = base_family) during automatic initialization and the resulting PDF has zero pages.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: Windows workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.154.0-alpha.6.1
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Only call graphics::par() when grDevices::dev.cur() is greater than 1; keep the selected family in options for devices opened later.

## Additional Notes
The same unconditional par call also exists in the optional showtext branch and should receive the same guard.
