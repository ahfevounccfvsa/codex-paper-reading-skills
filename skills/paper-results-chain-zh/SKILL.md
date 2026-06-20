---
name: paper-results-chain-zh
description: "Explain research paper experimental results in Chinese as a results chain: what data were used, what experiments were run, what numeric or visual results were obtained, how the authors interpreted those results, and what critical caveats remain. Use when the user asks to understand a paper's experiments, figures, tables, data results, result analysis, ablations, downstream tasks, or says prior summaries were too high-level and wants the actual evidence."
---

# Paper Results Chain Zh

## Overview

Use this skill to turn a paper's Results section into a clear Chinese explanation centered on evidence rather than general claims. The output should help the user see the chain:

`数据设计 -> 实验问题 -> 指标/图表 -> 结果数字或趋势 -> 作者解释 -> 批判性分析`.

## Source Handling

- Prefer full paper text, paper HTML, PDF text, tables, figure captions, supplementary tables, and available code/data links.
- If only abstract or limited text is available, explicitly say the explanation is limited and avoid inventing figure-level results.
- If the paper page embeds tables/figures as images, inspect captions and image/table files when possible.
- Distinguish exact numeric values from visual trends inferred from plots.
- Cite or mention the paper section/table/figure that supports each important result when possible.

## Reading Workflow

1. Identify the study question in one sentence.
2. Extract the data design:
   - samples, cell lines/species/subjects, treatments or conditions
   - number of compounds/classes/batches/plates/images/replicates when available
   - train/validation/test split and whether test data are held out by batch, compound, patient, time, plate, etc.
   - modalities and inputs/outputs
3. List each major experiment or result figure in order.
4. For each experiment, answer:
   - **它想证明什么**
   - **用了什么数据**
   - **比较了什么方法/条件**
   - **用了什么指标**
   - **得到什么结果**: include numbers if present; otherwise describe the trend carefully
   - **作者怎么解释**
   - **我的分析**: what the result supports, what it does not prove, and possible confounders
5. End with a compact synthesis:
   - strongest evidence
   - weakest or riskiest evidence
   - whether the paper's main claim is supported by the results
   - what to verify when reading the original figures/tables

## Output Format

Use Chinese by default. Prefer this structure unless the user asks otherwise:

```md
## 总体问题

一句话说明这篇论文到底想验证什么。

## 1. 数据设计

列出数据规模、样本/条件、模态、重复、划分方式和关键风险。

## 2. 实验结果链条

### 实验 1：短标题
- 想回答的问题：
- 数据与设置：
- 指标：
- 结果：
- 作者解释：
- 我的分析：

### 实验 2：短标题
...

## 3. 总结判断

- 哪些结果最支持主结论：
- 哪些结果只是辅助证据：
- 哪些混杂/不可辨识风险最大：
- 这篇文章适合怎么引用或使用：
```

## Explanation Rules

- Do not stop at "they did X"; always explain "what data/result shows X".
- Do not collapse all results into a single summary. Preserve the order of major experiments when it helps the user follow the paper.
- Explain metrics briefly when they matter to interpretation, especially if the user may not know them.
- For tables, report the most important values and contrast them directly.
- For plots, describe axes, grouping, thresholds, and what trend or cluster pattern matters.
- For ablations, state which component was removed or changed and what performance change implies.
- For downstream tasks, separate "fits the training task" from "generalizes to new tasks/data".
- For interpretability figures, separate biological interpretation from possible artifacts.

## Critical Checks

Always include caveats when relevant:

- batch/plate/site/patient leakage
- train/test split not independent enough
- class imbalance or too few samples per class
- repeated measurements from the same biological unit
- metrics that reward easy negatives or hide weak sensitivity
- visual similarity not matching downstream utility
- artifact-driven prediction rather than biological signal
- weak external validation or private/non-reproducible data

## Tone

Be concrete, patient, and evidence-centered. The user often wants help reading figures and tables, so make the result feel like walking through the paper with them, not like rewriting the abstract.
