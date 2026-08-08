# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: af193390da33898a95a4e3742e2000bad81cd49a643825f200ea94124633c40e
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-22T01:12:25Z
- Last seen at: 2026-07-22T01:12:25Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows wrapper decodes R subprocess output with GBK and crashes on UTF-8 bytes

## Expected Behavior
The wrapper should decode Rscript output robustly and report the actual render result.

## Actual Behavior
The render subprocess starts, but Python subprocess text decoding raises UnicodeDecodeError before the wrapper can report the R result.

## Reproduction Steps
- Run knit_rmd_html.py from a Windows GBK locale after pandoc is available.
- Render an Rmd whose R subprocess emits UTF-8 output.

## Evidence
- UnicodeDecodeError: 'gbk' codec cannot decode byte 0x80 in subprocess stdout.

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
Run the wrapper with Python -X utf8 so subprocess text decoding uses UTF-8.

## Additional Notes
None
