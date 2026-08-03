# Bug Report

## Metadata
- Skill: complete-example
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 7a1e1ca967d4a9f40fd8c6248bd0fb5acb64584dfe76635d723a96ab63e7bd58
- Severity: important
- Occurrence count: 1
- First seen at: 2026-07-16T15:07:16Z
- Last seen at: 2026-07-16T15:07:16Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
输入类 LaTeX 文件被强制要求使用并非所有模板都定义的 subsubsubsection 命令

## Expected Behavior
章节层级校验应根据目标项目实际定义的命令或语义等价标题进行适配，同时保护模板骨架并保持可编译。

## Actual Behavior
技能配置把 subsubsection 和 subsubsubsection 设为所有输入文件的强制字面要求；目标项目未定义 subsubsubsection，照做会触发 Undefined control sequence。

## Reproduction Steps
- 选择一个仅定义标准 LaTeX 层级、未定义 subsubsubsection 的现有模板项目。
- 按 complete-example 的 generation.section_hierarchy.generation_requirement 为输入文件同时加入两个命令。
- 使用 XeLaTeX 编译，观察 subsubsubsection 未定义错误。

## Evidence
- 目标项目配置中不存在 subsubsubsection 定义，而技能以 strict 模式要求每个输入文件包含该命令。

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex
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
使用目标项目原生的无编号粗体段落标题表达等价层级，并以实际编译成功作为优先验收条件。

## Additional Notes
None
