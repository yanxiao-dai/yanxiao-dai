# 文献总结审稿框架

Use this reference when writing the structured report. Treat the article as a journal submission that needs expert editorial reading, not as a simple abstract rewrite.

## 总体原则

- Separate article evidence from your inference or field comparison.
- Prefer precise wording: "作者证明了", "作者提出", "结果显示", "文章未说明".
- Keep numerical details, study area names, temporal ranges, dataset names, model names, indices, thresholds, and validation metrics whenever available.
- Do not invent missing values. Mark missing but important details as `未说明`, then explain why the omission matters.
- Output in Chinese unless the user requests another language. Retain key English terms in parentheses when they are useful for later searching.

## 推荐报告结构

### 文献基本信息

Include title, authors, journal/conference, year, DOI or URL if available, study area, study period, research object, and keywords. If metadata is missing from the extracted text, inspect the first pages of the source document.

### 摘要与全文总述

Summarize the whole paper in 1-3 paragraphs:

- Background and research question.
- Core method and data.
- Main result and conclusion.
- Why the paper matters.

### 引言：研究问题与研究目的

Extract:

- Scientific or practical problem the paper addresses.
- Field gap: unclear mechanism, data limitation, scale mismatch, index limitation, model limitation, application need, or policy/management need.
- Research objective, hypothesis, and questions.
- Claimed contribution relative to prior work.

### 方法：方法体系、创新方法与技术路线图

Summarize methods as a connected system:

1. Input data and preprocessing.
2. Indicator/index construction.
3. Event identification or sample selection.
4. Statistical, geospatial, machine learning, physical, or causal methods.
5. Validation, sensitivity analysis, uncertainty analysis.
6. Output products and interpretation.

Highlight method innovation when the article improves definitions, thresholds, fusion of datasets, spatial-temporal scaling, attribution, causal inference, model architecture, validation strategy, or operational application.

Write a textual technical route such as:

`数据获取 -> 预处理与质量控制 -> 指标计算 -> 事件识别 -> 驱动因子分析 -> 结果验证 -> 区域/季节/情景解释`

If useful, include a Mermaid flowchart in the Markdown report; otherwise describe the route in numbered steps so the Word document remains readable.

### 数据：数据集、年限、类型、来源、优势与处理

For every dataset, capture:

- Dataset/product name.
- Variable(s).
- Temporal range used by the article.
- Spatial range and resolution.
- Temporal resolution.
- Data type: station observation, reanalysis, satellite remote sensing, model simulation, survey, experimental, socio-economic, land cover, soil, vegetation, hydrological, or derived index.
- Source organization and website/portal when stated.
- Preprocessing: projection, resampling, interpolation, gap filling, masking, clipping, normalization, anomaly calculation, quality flags, temporal aggregation, detrending, standardization.
- Advantages: coverage, resolution, continuity, validation history, physical interpretability, multi-source complementarity, long time series, operational availability.
- Limitations: uncertainty, scale mismatch, missing values, retrieval error, station sparsity, model bias, cloud contamination, temporal inconsistency.

### 结果：逐标题总结

For each results subsection:

- State the subsection's question.
- Summarize the key finding.
- Identify the evidence: statistic, map pattern, time series, trend, model output, significance test, or comparison.
- Explain how it supports the paper's objective.
- Note uncertainty or exceptions.

### 图表解读：逐图逐表解释

For each figure/table:

- Identify purpose and content.
- Explain axes, variables, units, panels, legends, classes, or scenarios.
- Summarize the most important pattern or number.
- Link it to the result subsection and conclusion.
- Note whether the figure/table is descriptive, diagnostic, validation-focused, or explanatory.

If the extraction misses a caption, infer only from surrounding text and state that the caption was not fully available.

### 讨论：讨论角度与小标题展开

Identify what angle the discussion uses:

- Mechanism explanation.
- Comparison with previous literature.
- Regional differences.
- Seasonal or scale effects.
- Method uncertainty.
- Data uncertainty.
- Practical implications.
- Policy, management, ecological, agricultural, or risk-warning relevance.

If discussion has subheadings, summarize each subheading separately and explain how it extends the results.

### 结论：主要结论与证据链

Integrate abstract and conclusion:

- Main conclusion.
- Supporting evidence from methods/results.
- Generalization scope.
- Application value.
- Any final recommendation.

### 研究方向、创新点、意义与同领域优势

Summarize:

- Research direction and subfield.
- The article's innovation points.
- Significance for theory, method, data, monitoring, forecasting, risk management, ecological protection, agriculture, hydrology, climate adaptation, or policy.
- Advantages over same-field papers: stronger data, finer resolution, better validation, clearer mechanism, improved operationality, stronger transferability, or more complete uncertainty analysis.

### 近三年同类研究比较

When web search is allowed:

- Use the current date to define the last three years exactly.
- Search recent papers with the article's core keywords, method names, study region, and domain.
- Prefer journal pages, DOI pages, publisher pages, institutional pages, and Google Scholar-like metadata if accessible.
- Compare 3-6 relevant studies. Do not compare only by title; compare research problem, data, method, scale, conclusion, and novelty.
- Cite links used in the final report or in a references section.

### 不足、建议与未来工作

Make suggestions actionable:

- Data expansion or replacement.
- Longer time series or finer spatial-temporal resolution.
- Independent validation.
- Sensitivity and uncertainty analysis.
- Mechanism attribution.
- Cross-region transfer testing.
- Multi-model comparison.
- Operational early warning or management application.
- Code/data reproducibility.

Tie each suggestion to a specific limitation rather than listing generic improvements.
