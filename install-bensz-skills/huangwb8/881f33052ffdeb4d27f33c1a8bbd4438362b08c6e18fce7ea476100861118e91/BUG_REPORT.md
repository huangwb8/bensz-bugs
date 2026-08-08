# Bug Report

## Metadata
- Skill: install-bensz-skills
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 881f33052ffdeb4d27f33c1a8bbd4438362b08c6e18fce7ea476100861118e91
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-07-20T01:30:21Z
- Last seen at: 2026-07-20T01:30:21Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
Windows 远程安装完成后，清理临时 Git 克隆目录时因解码异常和文件锁退出失败

## Expected Behavior
远程检查安装完成后应清理临时目录并以成功状态退出

## Actual Behavior
两个目标均完成技能更新，但随后出现 GBK 解码异常和 WinError 5，安装器以退出码 1 结束，临时目录残留

## Reproduction Steps
- 在 Windows 默认 GBK 代码页下运行 install.py --remote --check --general
- 确认安装后等待安装器清理临时 Git 克隆目录

## Evidence
- subprocess reader reported UnicodeDecodeError for GBK; cleanup reported WinError 5 on a Git pack index file

## Environment Notes
- Skill source path: None
- Skill source repo: huangwb8/skills
- Device type: unknown
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex on Windows
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.144.0-alpha.4
  - gh: unavailable
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - python3: unavailable
  - rg: ripgrep 15.1.0 (rev af60c2de9d)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
确认安装摘要后，等待文件锁释放，再手动删除临时目录；已安装技能可正常使用

## Additional Notes
None
