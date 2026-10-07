# Bug Report

## Metadata
- Skill: init-project
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 0a30505283093f561e187d5ad19c2c0477f459aec2d1aeddf7bd46024acd9ada
- Severity: high
- Occurrence count: 1
- First seen at: 2026-08-08T13:20:49Z
- Last seen at: 2026-08-08T13:20:49Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Auto analysis misidentifies a README env-var example as the project name and overwrites existing agent-entry instructions during merge.

## Expected Behavior
Auto initialization derives a meaningful project name and preserves existing nonstandard but critical agent instructions during intelligent merge.

## Actual Behavior
The generated AGENTS.md title becomes an env-var comment and replaces the existing instruction to read AGENT_GUIDE.md.

## Reproduction Steps
- Run the initializer with --auto in a repository whose README contains an .env example before a conventional title parse succeeds.
- Use an existing AGENTS.md whose critical instructions are outside the generator standard Chinese headings.

## Evidence
- Generated title was derived from an env-var comment and the prior AGENT_GUIDE.md entry instruction was removed.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.144.0-alpha.4
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Review the diff, then manually restore project-specific agent entry rules and a correct project title.

## Additional Notes
None
