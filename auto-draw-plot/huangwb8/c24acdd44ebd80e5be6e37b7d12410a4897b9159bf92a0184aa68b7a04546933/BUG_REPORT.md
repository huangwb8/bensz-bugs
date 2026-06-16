# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: c24acdd44ebd80e5be6e37b7d12410a4897b9159bf92a0184aa68b7a04546933
- Severity: p1
- Occurrence count: 1
- First seen at: 2026-05-20T04:10:21Z
- Last seen at: 2026-05-20T04:10:21Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 provider does not reuse Codex local auth credentials

## Expected Behavior
auto-draw-plot should resolve both BenszAPI base URL and reusable credential from Codex local config files such as ~/.codex/config.toml and ~/.codex/auth.json when the user is running inside Codex.

## Actual Behavior
The provider resolver only reads base_url from Codex config and fails gpt-image-2 with a missing OPENAI_API_KEY / OPENAI_API message, then falls back to Nano Banana.

## Reproduction Steps
- Run python3 auto-draw-plot/scripts/nano_banana_check.py in an environment where Codex is authenticated but OPENAI_API_KEY is not exported.

## Evidence
- Warning: 图片 provider `gpt-image-2` 不可用，原因：缺少 OPENAI_API_KEY / OPENAI_API；Codex config 只提供 base_url，不提供可复用密钥

## Environment Notes
- Skill source path: None
- Skill source repo: pipelines/skills
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
- Key software versions:
  - claude: 2.1.119 (Claude Code)
  - codex: codex-cli 0.124.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Use Nano Banana fallback or explicitly export OPENAI_API_KEY until provider resolver reads Codex auth.json.

## Additional Notes
None
