# Bug Report

## Metadata
- Skill: nsfc-ref-alignment
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: d17979f0c36b6309fcf8a7abbede94bbabc9569294024a8e357625cbeada365b
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-06-22T15:19:26Z
- Last seen at: 2026-06-22T15:19:26Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
nsfc-ref-alignment fails to extract citations from projects using custom body input macros and default citation config

## Expected Behavior
The skill should discover included chapter files and extract standard LaTeX citations such as \\cite{...} from NSFC project sources.

## Actual Behavior
On a project where main.tex uses a custom wrapper macro like \\RegionalBodyInput{extraTex/1.立论依据.tex}, the generated report showed total_citations=0 even though the chapter contains many \\cite{...} calls; a warning also referenced extraTex/#1.tex.

## Reproduction Steps
- Run run_ref_alignment.py with --project-root . --main-tex main.tex --report-dir references --prepare --verify-online on a project using a custom wrapper macro for chapter input.
- Inspect the generated ref_integrity_report.md and observe total_citations=0 despite cited chapter content.

## Evidence
- ref_integrity_report.md: total_citations: 0; warning: missing tex file referenced: extraTex/#1.tex; chapter contains many \\cite{...} commands.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.181 (Claude Code)
  - codex: codex-cli 0.137.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Directly scan the target chapter for citation commands and parse the project BibTeX file, then perform DOI/title verification manually.

## Additional Notes
None
