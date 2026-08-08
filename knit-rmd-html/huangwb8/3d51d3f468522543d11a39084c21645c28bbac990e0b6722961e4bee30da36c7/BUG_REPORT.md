# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 3d51d3f468522543d11a39084c21645c28bbac990e0b6722961e4bee30da36c7
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T07:14:01Z
- Last seen at: 2026-08-01T07:14:01Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Python wrapper decodes R render output with Windows GBK and crashes on UTF-8 bytes

## Expected Behavior
The render wrapper should capture R subprocess output robustly on Windows and return the real render status.

## Actual Behavior
subprocess.run text mode uses the default GBK decoder and raises UnicodeDecodeError when R emits UTF-8 output, masking the render result.

## Reproduction Steps
- Run knit_rmd_html.py on a UTF-8 R Markdown report from a Windows GBK console.

## Evidence
- UnicodeDecodeError: GBK codec cannot decode a UTF-8 byte while subprocess stdout is being read.

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
Run the wrapper with PYTHONUTF8=1 so Python subprocess text decoding uses UTF-8 mode.

## Additional Notes
None
