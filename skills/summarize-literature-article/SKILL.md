---
name: summarize-literature-article
description: Use when Codex needs to read an uploaded journal article in PDF or Word (.pdf, .docx, .doc), extract its content, review it from a journal literature expert/editor perspective, summarize introduction, methods, data, results, figures, tables, discussion, conclusion, abstract, innovations, field significance, limitations, future work, optionally compare related studies from the most recent three years, and output a structured Chinese Word (.docx) literature summary report.
---

# Summarize Literature Article

## Overview

Use this skill to turn one or more uploaded journal papers into a structured Chinese Word literature summary. Read the paper as a critical journal editor: distinguish what the paper proves, what it only claims, what is missing, and why the work matters in its research field.

## Workflow

1. Confirm inputs: source article file(s), desired output path, and whether the user wants cross-paper comparison. If the user does not specify an output path, create a `.docx` beside the source file or in the current workspace.
2. Extract text and metadata with `scripts/extract_document_text.py`. Use the extracted Markdown as the working source, but inspect the original file when captions, tables, equations, or section order look incomplete.
3. Read `references/review_framework.md` before writing the report. If the paper concerns drought, flash drought, climate extremes, hydrology, vegetation stress, remote sensing, or agro-meteorology, also read `references/drought_flash_drought_checklist.md`.
4. Reconstruct the article structure: title, journal/year if available, abstract, introduction, methods, data, results, figures/tables, discussion, conclusion, references that matter, and supplementary notes if present.
5. Produce a Chinese analytical report following the framework. Keep the original technical terms in parentheses when useful. Use `未说明` only when the article genuinely does not provide the information.
6. For "近三年同类文章比较", browse/search current scholarly sources unless the user explicitly forbids web access. Use concrete publication years based on the current date, compare methods/data/novelty, and cite sources or links used. Clearly label inferences that come from comparison rather than from the target paper.
7. Convert the final Markdown report to Word with `scripts/build_literature_summary_docx.py`. If a richer Word layout, tracked comments, or page-render verification is requested, use the available document/DOCX workflow after this script.
8. Verify the Word file exists and that the required sections are present before responding.

## Extraction

Run with a Python environment that has `pypdf` and `python-docx` installed. On this user's machine, first try `D:\minicoda\python.exe`; if dependencies are missing, use the bundled Codex Python runtime or install the packages listed in `scripts/requirements.txt`.

```bash
python scripts/extract_document_text.py "<article.pdf-or-docx>" --out "<article_extracted.md>" --metadata "<article_metadata.json>"
```

Use the bundled Python runtime if the system `python` is unavailable. The extractor supports `.pdf` and `.docx`; for legacy `.doc`, convert to `.docx` first if a converter is available, otherwise ask the user for a `.docx` or PDF copy. If a scanned PDF yields very little text, report that OCR is required before analysis.

## Report Writing

Write the report as Markdown first. Required top-level sections:

- 文献基本信息
- 摘要与全文总述
- 引言：研究问题与研究目的
- 方法：方法体系、创新方法与技术路线图
- 数据：数据集、年限、类型、来源、优势与处理
- 结果：逐标题总结
- 图表解读：逐图逐表解释
- 讨论：讨论角度与小标题展开
- 结论：主要结论与证据链
- 研究方向、创新点、意义与同领域优势
- 近三年同类研究比较
- 不足、建议与未来工作

For each figure/table, explain: what it shows, variables/axes/panels, spatial-temporal scope, key pattern, how it supports the article's claim, and any uncertainty or limitation.

## Word Output

Run with the same Python environment:

```bash
python scripts/build_literature_summary_docx.py --markdown "<summary.md>" --out "<summary.docx>" --title "文献总结报告"
```

Use concise headings, evidence-based paragraphs, and bullet lists only where they improve readability. Do not paste long untranslated source text from the article; summarize in Chinese and quote only short phrases when necessary.

## Quality Gate

Before final delivery, check:

- Every requested article section is covered.
- Methods and data summaries are not mixed together.
- Dataset names, periods, variables, resolution, source websites, and preprocessing are explicit where available.
- Innovative methods and the complete technical route are highlighted.
- Each result heading and each figure/table has a separate interpretation.
- Limitations and future work are concrete enough to guide the user's next research.
- The `.docx` report was created successfully.
