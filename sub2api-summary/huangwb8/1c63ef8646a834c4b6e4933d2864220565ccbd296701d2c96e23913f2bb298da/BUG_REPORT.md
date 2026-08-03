# Bug Report

## Metadata
- Skill: sub2api-summary
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 1c63ef8646a834c4b6e4933d2864220565ccbd296701d2c96e23913f2bb298da
- Severity: high
- Occurrence count: 1
- First seen at: 2026-07-24T06:59:03Z
- Last seen at: 2026-07-24T06:59:03Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
脱敏采集遗漏 user 字段中的邮箱

## Expected Behavior
所有响应位置的邮箱和身份标识均被稳定标记替换后再写入本地数据目录。

## Actual Behavior
递归脱敏仅按字段名含 email 或身份字段表处理；支付仪表盘响应的 user 字段含邮箱时被原样写入。

## Reproduction Steps
- 使用 collect_sub2api_data.py 采集包含 payment_dashboard 响应的管理员只读数据。
- 检查输出 JSON 中 user 字段；可见未替换的邮箱字符串。

## Evidence
- sanitize_payload 调用递归字段名规则，但 user 不在身份字段名单中；该字段的字符串邮箱未被识别。

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: unknown
- OS: Darwin / 25.5.0 / arm64
- Shell: /bin/zsh
- Agent runtime: codex
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
在继续分析前移除受影响响应文件；修复前不要把该文件作为可安全脱敏产物保留或共享。

## Additional Notes
None
