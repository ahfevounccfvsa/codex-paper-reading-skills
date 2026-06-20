---
name: paper-reading
description: Rapidly interpret research papers, abstracts, notes, or extracted article text into a rigorous Chinese reading brief. Use when the user wants to quickly understand what a paper does, why it matters, how it works, what the experiments show, where the weaknesses are, and what to verify while reading.
---

# Paper Reading

Use this skill when the user wants a fast but reliable paper interpretation rather than a full translation.

This skill is designed for:
- arXiv abstracts
- full paper text extracted from PDF
- Obsidian paper notes
- pasted article sections such as abstract, introduction, method, or experiments

## Goal

Produce a structured Chinese reading brief that helps the user answer:
- 这篇文章做了什么
- 为什么要做
- 具体怎么做
- 实验结果说明了什么
- 这篇文章哪里强，哪里不够强
- 读正文时应该重点查什么

## Core Rules

1. Never invent datasets, baselines, metrics, numeric gains, or conclusions not supported by the provided text.
2. Separate facts from inference.
3. If the evidence is only from the abstract, say so explicitly.
4. Prefer clarity over hype.
5. Always include at least one critical reading section, even for strong papers.

## Source Priority

Use the richest available source in this order:
1. Full paper text or long extracted body text
2. Title + abstract + method/experiment sections
3. Title + abstract only

When only the abstract is available, state that the interpretation is abstract-level and mark missing details as not explicit in the abstract.

## Output Format

Unless the user asks for another format, use this structure:

```md
# 论文速读

## 一句话结论

## 这篇文章做了什么

## 研究背景与问题

## 方法核心
- 输入是什么
- 模型或系统由哪些部分组成
- 训练或推理流程是什么
- 相比已有方法新在哪里

## 实验与结果
- 任务与数据
- 比较对象
- 主要结果
- 结果意味着什么

## 这篇文章的贡献

## 局限与风险

## Critical Reading
- 做得好的地方
- 可能不够好的地方
- 为什么这会影响说服力
- 阅读正文时重点核查什么

## 适合怎么用这篇文章
```

## Reading Workflow

### Abstract-only mode

Use when only title and abstract are available.

Focus on:
- problem setting
- claimed method idea
- claimed result signal
- what remains unclear

Do not pretend to know:
- full architecture details
- exact training recipe
- ablation findings
- real generalization strength

### Full-text mode

Use when introduction, method, experiments, or full extracted text are available.

Read in this order:
1. title + abstract
2. introduction: identify motivation and problem framing
3. method: identify pipeline, modules, assumptions, and novelty
4. experiments: identify datasets, baselines, metrics, main tables, ablations, failure cases
5. conclusion/discussion: identify scope and limitations

Then synthesize the answer around:
- problem
- method
- evidence
- contribution
- weakness

## What To Look For

### For method papers
- Is the novelty real, or mostly engineering packaging?
- Which module likely drives the gain?
- Are the comparisons fair and recent?
- Are there ablations isolating the claimed contribution?

### For benchmark or dataset papers
- Is the task definition meaningful?
- Does the benchmark reflect real use cases?
- Are evaluation metrics aligned with the claimed goal?
- Could the benchmark be gamed?

### For medical AI papers
- Is the task clinically meaningful?
- Is the supervision realistic?
- Are external validation, robustness, and deployment assumptions discussed?
- Is interpretability genuine or just extra outputs?

### For LLM or agent papers
- Does the improvement come from the core method, larger compute, or tool scaffolding?
- Are prompts, tools, and retrieval settings comparable to baselines?
- Is the evaluation sensitive to contamination or task design bias?

## Style

- Write in clear professional Chinese.
- Sound like a careful advisor, not marketing copy.
- Be specific when evidence is present.
- Be explicit about uncertainty when evidence is missing.

## Optional Closing

If useful, end with a short recommendation:
- 值得精读
- 值得略读
- 适合作为思路参考
- 目前说服力一般
