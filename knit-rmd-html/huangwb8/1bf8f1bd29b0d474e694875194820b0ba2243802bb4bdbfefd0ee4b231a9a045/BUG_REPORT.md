# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 1bf8f1bd29b0d474e694875194820b0ba2243802bb4bdbfefd0ee4b231a9a045
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-14T23:42:35Z
- Last seen at: 2026-07-14T23:42:35Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows render wrapper fails when decoding non-GBK R output

## Expected Behavior
The wrapper should render an Rmd report when R and Pandoc are available.

## Actual Behavior
The wrapper exits with UnicodeDecodeError while decoding R process output before reporting render status.

## Reproduction Steps
- Run the wrapper on Windows with Rscript and Pandoc available in PATH.
- Render an Rmd whose R process emits UTF-8 output.

## Evidence
- UnicodeDecodeError: gbk codec cannot decode byte 0x80 while subprocess output is read.

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
Invoke rmarkdown::render directly with UTF-8 output encoding and the same knit root directory.

## Additional Notes
None
