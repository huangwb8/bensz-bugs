# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 732354392ab2f260e4481858c4707b6da4edfb35117b78ab00e0524e59c533d6
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-07T12:26:26Z
- Last seen at: 2026-08-07T12:26:26Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
dedupe_papers.py splits valid JSONL records on Unicode line separator U+2028

## Expected Behavior
The deduplication stage should parse each newline-delimited JSON record emitted by multi_query_search.py.

## Actual Behavior
A valid JSONL record containing U+2028 in an abstract is split by str.splitlines(), causing JSONDecodeError: Unterminated string.

## Reproduction Steps
- Run multi-query search where one OpenAlex abstract contains U+2028.
- Pass the emitted valid JSONL file to dedupe_papers.py.

## Evidence
- 500 records pass jq and physical-line json.loads; one record contains ten U+2028 characters; dedupe_papers.py fails at column 2470 after splitlines().

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
Replace U+2028/U+2029 inside JSON strings with escaped newline sequences before deduplication, then validate every record and rerun stage 2.

## Additional Notes
None
