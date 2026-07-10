# Bug Report

## Metadata
- Skill: nsfc-ref-alignment
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 028733f3a73d1d9086afa60e83c819d89d4df3c1fb697b9dc8f91d1b20fb84b6
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-05T06:15:39Z
- Last seen at: 2026-07-05T06:15:39Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
verify-online crashes on Python 3.12 because inline regex flag is not at pattern start

## Expected Behavior
run_ref_alignment.py --verify-online should complete DOI online verification or degrade gracefully.

## Actual Behavior
The script raises re.error: global flags not at the start of the expression at position 1 in online_verify.py when normalizing DOI strings.

## Reproduction Steps
- Run python3 nsfc-ref-alignment/scripts/run_ref_alignment.py --project-root . --main-tex main.tex --report-dir references --prepare --verify-online under Python 3.12.

## Evidence
- Traceback points to re.sub(r"^(?i)\s*doi\s*:\s*", "", doi_norm) in online_verify.py; Python 3.12 rejects inline (?i) after ^.

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
Run without --verify-online for deterministic structure checks; perform DOI spot checks separately via Crossref/DOI resolver or subagent review.

## Additional Notes
None
