# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: fc0e7699bce1fb2efde5ad45d83815541c5eec367dbb75a3bbe6b00025d49767
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-16T07:47:33Z
- Last seen at: 2026-07-16T07:47:33Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Python wrapper decodes R render output with Windows GBK locale

## Expected Behavior
The wrapper should capture UTF-8 R output without crashing on Windows.

## Actual Behavior
subprocess text decoding uses the GBK locale and raises UnicodeDecodeError when R emits UTF-8 output.

## Reproduction Steps
- Run knit_rmd_html.py from default Windows PowerShell on an Rmd whose render output contains non-ASCII text.

## Evidence
- UnicodeDecodeError: 'gbk' codec cannot decode byte 0x80

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
Set PYTHONUTF8=1 before invoking the wrapper.

## Additional Notes
None
