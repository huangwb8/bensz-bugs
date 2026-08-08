# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 63c3dd15043505ed1a0ebe37104e5d1060eaa53a8ce7f784ac945a25df1bcb07
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-07T12:50:45Z
- Last seen at: 2026-08-07T12:50:45Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
BibTeX generator preserves literal backslash-n sequences from metadata and creates invalid LaTeX commands

## Expected Behavior
BibTeX metadata cleaning should normalize encoded line breaks so generated references compile.

## Actual Behavior
Thirty literal backslash-n sequences remained in titles and abstracts; XeLaTeX failed with Undefined control sequence at the generated bibliography.

## Reproduction Steps
- Select a paper whose upstream title or abstract contains encoded backslash-n text.
- Generate BibTeX and compile the review with xelatex and bibtex.

## Evidence
- Compilation failed at a bibliography title containing Natural backslash-n Language Inference; replacing literal backslash-n with spaces preserved 150 entries and allowed PDF export.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: desktop
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python3: 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Normalize literal backslash-n sequences to spaces in the task BibTeX file, validate entry count, and rerun export.

## Additional Notes
None
