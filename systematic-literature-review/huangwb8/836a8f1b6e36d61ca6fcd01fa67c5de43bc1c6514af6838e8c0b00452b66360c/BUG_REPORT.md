# Bug Report

## Metadata
- Skill: systematic-literature-review
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 836a8f1b6e36d61ca6fcd01fa67c5de43bc1c6514af6838e8c0b00452b66360c
- Severity: high
- Occurrence count: 1
- First seen at: 2026-04-10T07:22:10Z
- Last seen at: 2026-04-10T07:22:10Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
OpenAlex 检索默认接受 br 压缩导致分页请求在当前 requests/urllib3/brotli 环境下稳定解码失败

## Expected Behavior
阶段1 检索应能稳定从 OpenAlex 拉取 JSON 结果并生成 papers.jsonl

## Actual Behavior
openalex_search.py 使用 requests 默认 Accept-Encoding，收到 br 响应后在分页请求中抛出 ContentDecodingError，导致 pipeline 阶段1失败

## Reproduction Steps
- 在 pipelines/reviews 中运行 pipeline_runner.py，topic=近端胃双通道手术-01，domain=clinical，显式传入 --work-dir
- 阶段1 调用 openalex_search.py 后抛出 requests.exceptions.ContentDecodingError

## Evidence
- Received response with content-encoding: br, but failed to decode it

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.3.0 / arm64
- Shell: /bin/zsh
- Agent runtime: Codex CLI
- Key software versions:
  - claude: 2.1.50 (Claude Code)
  - codex: codex-cli 0.104.0
  - gh: unavailable
  - git: git version 2.50.1 (Apple Git-155)
  - node: v24.11.1
  - npm: 11.6.2
  - python3: Python 3.13.11
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
在检索请求中显式设置 Accept-Encoding=gzip, deflate，或在任务目录中用本地脚本生成 papers_*.jsonl 后从阶段2继续

## Additional Notes
None
