# Bug Report

## Metadata
- Skill: research-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 30441ec4ad79ef05359b987a3d6eaa465a404237c803663f34617a23a97cc58e
- Severity: medium
- Occurrence count: 2
- First seen at: 2026-08-07T12:18:54Z
- Last seen at: 2026-08-07T12:22:05Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
多查询检索输出含不完整 JSONL 记录导致去重阶段中止

## Expected Behavior
多查询检索完成后应生成逐行可独立解析的 JSONL，去重阶段应能读取全部有效记录并继续

## Actual Behavior
检索报告写出 500 条候选记录，但 dedupe_papers.py 解析时触发 JSONDecodeError: Unterminated string，Pipeline 在阶段 2 中止

## Reproduction Steps
- 准备 15 组跨符号回归、Prompt 偏移和长程智能体的 OpenAlex 查询
- 运行 run_pipeline.py 至检索和去重阶段
- 观察 papers JSONL 中至少一行不完整，去重脚本中止
- 观察 papers JSONL 中含 U+2028/U+2029 等合法 Unicode 行分隔符；逐行读取可解析，但 read_text().splitlines() 会在 JSON 字符串内部切断记录

## Evidence
- JSONDecodeError: Unterminated string starting at line 1 column 912; dedupe stage exit 1
- JSONDecodeError: Unterminated string starting at line 1 column 912; 过滤 U+0085/U+2028/U+2029 后同一去重命令成功：500 输入、488 输出

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.6.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: 2.1.205 (Claude Code)
  - codex: codex-cli 0.144.0
  - gh: gh version [redacted:phone])
  - git: git version 2.50.1 (Apple Git-155)
  - node: v22.11.0
  - npm: 10.9.0
  - python3: Python 3.9.6
  - rg: ripgrep 15.1.0

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
保留原始 JSONL 后，将 U+0085/U+2028/U+2029 正规化为空格，再运行去重；长期修复应以文件对象逐行迭代替代 read_text().splitlines()

## Additional Notes
根因已定位：dedupe_papers.load_papers 使用 str.splitlines()，会把 JSON 字符串内合法的 Unicode 行分隔符误判为记录边界。
