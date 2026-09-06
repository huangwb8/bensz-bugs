# Bug Report

## Metadata
- Skill: knit-rmd-html
- Skill author: Bensz Conan
- Reporter GitHub: huangwb8
- Bug hash: 3b2860bc6beeac573bf4707f9e003bf2216d8c203b6e887ffb0c7765cec820bc
- Severity: medium
- Occurrence count: 1
- First seen at: 2026-09-06T15:19:01Z
- Last seen at: 2026-09-06T15:19:01Z
- Privacy: Sensitive user data is auto-redacted before storage and public reporting.

## Summary
R Markdown renderer does not preserve Unicode output when Windows R locale is C

## Expected Behavior
Rendered HTML should retain real UTF-8 Chinese and other Unicode characters in code output, inline results, and document text.

## Actual Behavior
With Windows Rscript locale C, R/knitr output is serialized as <U+XXXX>; Pandoc escapes it to &lt;U+XXXX&gt;, so the HTML displays literal Unicode placeholders.

## Reproduction Steps
- Run the knit-rmd-html renderer for a Chinese Rmd on Windows with Rscript locale C.
- Include Chinese text in emitted output or inline/document content.
- Inspect the generated HTML and observe literal <U+XXXX> or &lt;U+XXXX&gt; placeholders.

## Evidence
- 02-ablation03-experiment.html initially contained many literal Unicode placeholders; R locale reported C; after document/output hooks decode placeholders and rerender, placeholder counts are zero.

## Environment Notes
- Skill source path: redacted
- Skill source repo: None
- Device type: Windows
- OS: Windows / 11 / AMD64
- Shell: unknown
- Agent runtime: Codex
- Key software versions:
  - claude: unavailable
  - codex: codex-cli 0.153.0
  - gh: gh version [redacted:phone])
  - git: git version 2.45.1.windows.1
  - node: v21.7.1
  - npm: unavailable
  - pandoc: via rmarkdown
  - python3: unavailable
  - r: 4.3.1
  - rg: ripgrep 15.2.0 (rev e89fff89ac)

## Impact
这是由 skill 设计缺陷导致的真实环境问题，需要纳入后续修复闭环。

## Workaround
Set knitr encoding to UTF-8 and decode <U+XXXX> plus HTML-escaped placeholders in knitr output/text/document hooks before Pandoc.

## Additional Notes
The issue is in rendering-chain locale/encoding handling, not in bensz-rmd-rules content guidance. Local report only; no public upload requested.
