# Bug Report

## Metadata
- Skill: install-bensz-skills
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 59e987baabdfeb75a1973b9b760c2194782f594e698380556dc487783902193a
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-04T07:10:19Z
- Last seen at: 2026-07-04T07:10:19Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Remote source filter with hyphenated source id is not applied

## Expected Behavior
Running remote check with --anthropic-docs should select only the anthropic-docs remote source.

## Actual Behavior
The command accepted --anthropic-docs but still prompted through all configured remote sources instead of selecting only Anthropic docs.

## Reproduction Steps
- Run the installer in remote check mode with the --anthropic-docs source flag.
- Observe that it asks whether to install the general and research sources before the Anthropic docs source.

## Evidence
- Help lists --anthropic-docs, but filtered run did not show Selected sources: Anthropic docs and entered all-source prompts.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: 2.1.181 (Claude Code)
  - codex: codex-cli 0.137.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - install-bensz-skills: 0.5.7
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Answer no for unrelated sources, then answer yes for the Anthropic docs source.

## Additional Notes
None
