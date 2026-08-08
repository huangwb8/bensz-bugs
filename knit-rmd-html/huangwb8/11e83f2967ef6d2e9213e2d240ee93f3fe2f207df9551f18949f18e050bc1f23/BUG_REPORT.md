# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 11e83f2967ef6d2e9213e2d240ee93f3fe2f207df9551f18949f18e050bc1f23
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-22T06:38:20Z
- Last seen at: 2026-07-22T06:38:20Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows wrapper decodes R render output with the default GBK codec

## Expected Behavior
The wrapper should decode Rscript output robustly and finish rendering when the report emits UTF-8 bytes.

## Actual Behavior
subprocess.run uses text mode without an explicit encoding, so Windows GBK decoding raises UnicodeDecodeError on UTF-8 R output.

## Reproduction Steps
- Run knit_rmd_html.py on Windows with Rscript and Pandoc available.
- Render an Rmd whose R startup or package output contains UTF-8 bytes not valid in GBK.

## Evidence
- UnicodeDecodeError from subprocess communication while decoding Rscript stdout with the GBK codec.

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
Run the wrapper with Python UTF-8 mode using python -X utf8.

## Additional Notes
None
