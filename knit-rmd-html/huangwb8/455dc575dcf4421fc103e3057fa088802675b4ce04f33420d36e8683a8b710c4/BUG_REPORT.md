# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 455dc575dcf4421fc103e3057fa088802675b4ce04f33420d36e8683a8b710c4
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-09-06T16:03:59Z
- Last seen at: 2026-09-06T16:03:59Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows R rendering does not normalize an unsupported C.UTF-8 locale

## Expected Behavior
Rendering should preserve Unicode output on the documented Windows R workflow.

## Actual Behavior
R 4.3.1 rejects C.UTF-8, falls back to the C locale, and prints Unicode characters as escaped byte sequences in report output.

## Reproduction Steps
- Set LC_ALL, LC_CTYPE, and LANG to C.UTF-8 on Windows.
- Run the wrapper with R 4.3.1 and print Unicode text from an R chunk.

## Evidence
- R startup reports failed C.UTF-8 locale categories; before normalization, Unicode is emitted as octal byte escapes.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.153.0
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - r: 4.3.1
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
On Windows, set LC_CTYPE to Chinese_China.utf8 before report code executes, or normalize the child-process locale in the wrapper.

## Additional Notes
None
