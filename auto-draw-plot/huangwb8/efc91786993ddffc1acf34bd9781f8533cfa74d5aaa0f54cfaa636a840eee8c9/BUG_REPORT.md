# Bug Report

## Metadata
- Skill: auto-draw-plot
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: efc91786993ddffc1acf34bd9781f8533cfa74d5aaa0f54cfaa636a840eee8c9
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-08-04T15:28:10Z
- Last seen at: 2026-08-04T15:28:10Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
gpt-image-2 参考图编辑未把 image 传入异步 edits 请求

## Expected Behavior
传入有效 reference-image 后，异步图片编辑请求应包含该图片并进行保真微调。

## Actual Behavior
主流程识别到参考图并进入编辑端点，但服务端返回 invalid_images_edit_request: image is required。

## Reproduction Steps
- 先成功生成一张 JPEG 图片。
- 再次运行主入口并传入 reference-image 指向该 JPEG。
- 观察异步 edits 任务失败且报告缺少 image。

## Evidence
- ProviderJobError: invalid_images_edit_request; message=image is required

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
  - python: 3
  - python3: Python 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
不使用参考图编辑，改为把事实修正规则写成纯文本硬约束后重新生成；不切换 provider。

## Additional Notes
None
