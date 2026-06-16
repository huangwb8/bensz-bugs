# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 870f29e95a18a9fc24cc7e518ebb8bec526d69dcdbeaf6c7a5ce02710422306e
- Severity: high
- Occurrence count: 1
- First seen at: 2026-06-06T14:08:09Z
- Last seen at: 2026-06-06T14:08:09Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
指定 gpt-image-2 时文本规划和视觉评估仍调用 Gemini，导致未配置 Gemini 的用户链路异常

## Expected Behavior
用户指定 gpt-image-2 出图时，脚本文本规划应使用本地模板或由宿主 AI 负责，不应要求配置 Gemini；视觉评估也不应硬依赖 Gemini。

## Actual Behavior
run_draw_plot.py 的 build_round_prompt 和 evaluate_image 会加载 Gemini 配置并调用 generate_text，日志出现 Gemini header 认证回退；未配置 Gemini 时只能异常回退。

## Reproduction Steps
- 运行 auto-draw-plot 主脚本并传入 --provider gpt-image-2。
- 观察每轮 prompt-planner-debug 或 evaluation-debug 中出现 Gemini 请求，或日志出现 Gemini header 认证回退。

## Evidence
- run_draw_plot.py 调用 load_gemini_config/generate_text 构造 prompt；evaluate_image.py 调用 load_gemini_config/generate_text 做评估。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.167 (Claude Code)
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
当前先依赖本地模板 fallback 和启发式评估；正式修复应默认关闭脚本内 Gemini 文本规划/评估。

## Additional Notes
None
