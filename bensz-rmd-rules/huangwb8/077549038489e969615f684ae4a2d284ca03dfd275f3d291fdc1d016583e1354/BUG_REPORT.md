# Bug Report

## Metadata
- Skill: bensz-rmd-rules
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 077549038489e969615f684ae4a2d284ca03dfd275f3d291fdc1d016583e1354
- Severity: important
- Occurrence count: 1
- First seen at: 2026-08-01T07:16:48Z
- Last seen at: 2026-08-01T07:16:48Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
PDF preview helper lacks PNG fallback when Poppler is built without JPEG support

## Expected Behavior
PDF to JPG delivery should succeed when Poppler can rasterize PNG and ImageMagick can convert PNG to JPG.

## Actual Behavior
The helper tries only Poppler JPEG flags; TeX Live Poppler rejects them, then ImageMagick direct PDF reading fails, so the helper stops despite an available two-step backend.

## Reproduction Steps
- Use a Windows TeX Live Poppler build whose pdftoppm supports PNG but not JPEG.
- Call bensz_pdf_to_jpg with ImageMagick available but direct PDF reading restricted.

## Evidence
- Both Poppler commands exit with usage because the JPEG option is unsupported; direct ImageMagick PDF conversion also fails.

## Environment Notes
- Skill source path: None
- Skill source repo: None
- Device type: Windows workstation
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
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
Rasterize PDF to a temporary PNG with pdftocairo or pdftoppm, then convert that PNG to JPG with ImageMagick and remove the temporary PNG.

## Additional Notes
None
