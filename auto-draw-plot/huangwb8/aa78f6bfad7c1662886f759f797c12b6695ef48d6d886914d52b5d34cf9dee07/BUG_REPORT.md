# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: aa78f6bfad7c1662886f759f797c12b6695ef48d6d886914d52b5d34cf9dee07
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-18T09:55:48Z
- Last seen at: 2026-07-18T09:55:48Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 请求无法显式指定最低画质

## Expected Behavior
主入口应允许选择受支持的图片质量，并让生成与编辑请求都显式携带 quality=low。

## Actual Behavior
主入口没有 quality 参数，生成和编辑请求体只包含 model、prompt、size 与 n，无法验证最低画质要求。

## Reproduction Steps
- 查看 run_draw_plot.py 的 CLI 参数，确认不存在 quality。
- 追踪 image_provider_client.py 的 generations 与 edits 请求体，确认未携带 quality。

## Evidence
- 连通性检查成功，但真实请求构造阶段缺失 quality 字段；当前测试无法证明最低画质约束。

## Environment Notes
- Skill source path: None
- Skill source repo: https://github.com/huangwb8/skills
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v25.6.1
  - npm: 11.11.0
  - python3: Python 3.12.7
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
在源仓库中增加受约束的 quality 数据流和回归测试后，再用本地 Codex 配置复测。

## Additional Notes
None
