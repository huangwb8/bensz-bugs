# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 7fb353667f1f1adfcc1de67d5c8f48ebb826c4a5894970baae66f61cb0454237
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-05-20T07:12:35Z
- Last seen at: 2026-05-20T07:12:35Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
auto-draw-plot 在 Python 3.9 下因缺少 tomllib 无法读取 Codex BenszAPI provider 配置

## Expected Behavior
无论从 skill 目录还是上级项目目录运行，脚本都应稳定读取 Codex 配置或提供 Python 3.9 兼容 fallback，从而按优先级选择 gpt-image-2。

## Actual Behavior
从 auto-draw-plot 目录运行时 python3 为 3.9，import tomllib 失败后配置解析静默退化为空，主入口读不到 BenszAPI base URL 并回退到 nano_banana。

## Reproduction Steps
- 进入 auto-draw-plot skill 目录。
- 运行 python3 scripts/nano_banana_check.py。
- 观察到 gpt-image-2 provider 不可用并回退到 nano_banana；在上级 skills 目录用 Python 3.12 运行同一检查可选择 gpt-image-2。

## Evidence
- warning: 缺少 OPENAI_BASE_URL / OPENAI_API_BASE，且未从 Codex 配置找到 BenszAPI base_url；python3 --version 在 skill 目录为 3.9.6。

## Environment Notes
- Skill source path: None
- Skill source repo: None
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
  - python: 3.9.6
  - python3: Python 3.12.7
  - python_alt: 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
使用 Python 3.12 运行脚本，或显式提供 OPENAI_BASE_URL / OPENAI_API_BASE 环境变量。

## Additional Notes
None
