# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 651155894d24f863b3ffd8b7d8b5a168fb7e55ae65be6bde733437be383c1faf
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-11T09:41:39Z
- Last seen at: 2026-07-11T09:41:39Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows wrapper decodes UTF-8 R render output as GBK and crashes

## Expected Behavior
The wrapper should decode subprocess output robustly and complete rendering when R emits UTF-8 text.

## Actual Behavior
After Pandoc and Rscript are found, subprocess output decoding raises UnicodeDecodeError with the Windows GBK codec.

## Reproduction Steps
- Expose local Pandoc and Rscript on PATH.
- Run knit_rmd_html.py on an Rmd whose startup emits UTF-8 text.

## Evidence
- UnicodeDecodeError: gbk codec cannot decode byte 0x80 while reading subprocess stdout.

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
Run Python in UTF-8 mode or invoke the same rmarkdown::render expression directly with UTF-8 locale variables.

## Additional Notes
None
