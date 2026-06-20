---
name: paper-speedread-zh
description: Write Chinese paper-reading briefs in a high-information, readable style with a strong one-sentence takeaway, intuitive explanation of what the paper really does, concrete method details, key experiment numbers, critical reading, and practical framing. Use when the user wants a paper explained in the style of "论文速读" rather than a dry summary or literal translation.
---

# Paper Speedread ZH

Use this skill when the user wants a Chinese paper interpretation in the specific "论文速读" style:
- readable but not shallow
- structured but not stiff
- includes judgment and intuition
- preserves key technical details and representative numbers
- answers "这篇论文究竟做了什么" quickly

This skill is especially suitable for:
- arXiv papers the user wants explained in Chinese
- Zotero paper notes
- research reading notes for Obsidian or Markdown
- users who dislike abstract-only, compressed summaries

## Goal

Produce a Chinese reading note that feels like a strong lab-mate explanation, not a generic abstract paraphrase.

The note should help the user quickly grasp:
- 这篇文章到底在解决什么问题
- 为什么原来的设定/方法不够好
- 作者真正提出了什么
- 方法最关键的设计选择是什么
- 实验结果到底说明了什么
- 这篇文章值不值得继续精读

## Output Style

Write in clear, natural Chinese.

Target style:
- Lead with a strong high-level judgment.
- Explain the paper as if orienting a smart peer.
- Use concrete framing such as "这篇文章说的是…" "你可以把它理解成…" when helpful.
- Keep technical details that matter; do not flatten the method into vague buzzwords.
- Include representative metrics or table values when available.
- Include critical evaluation, not just praise.

Avoid:
- stiff template language
- empty praise
- abstract-only paraphrasing that never says what the paper really does
- exhaustive section-by-section translation
- invented datasets, metrics, or gains

## Preferred Structure

Unless the user requests otherwise, use this structure:

```md
# 论文速读

论文是 **Title**，Author1, Author2, Venue Year。它的核心价值是：**...**

来源：
- 论文 PDF: ...
- arXiv / project page: ...

## 一句话结论

## 这篇文章做了什么

## 方法核心

## 你可以怎么理解这套方法

## 实验结果说明了什么

## 这篇文章的贡献

## 局限与风险

## Critical Reading

## 适合怎么用这篇文章
```

Notes:
- The opening paragraph should carry real information, not just metadata.
- "方法核心" should explain both the pipeline and why the design choice matters.
- "你可以怎么理解这套方法" should translate the method into an intuitive mental model.
- "实验结果说明了什么" should not just list tables; interpret what the numbers imply.
- "Critical Reading" should say what to trust, what to doubt, and what to verify in the paper.

## Workflow

### 1. Establish paper identity and scope

Extract when available:
- title
- authors
- venue/year
- primary source links

If venue is unclear, say so.
If only the abstract is available, explicitly say the reading is abstract-level.

### 2. Find the paper's real problem framing

Answer in plain language:
- What task or setting is being studied?
- What unrealistic assumption in prior work is the paper criticizing or relaxing?
- Why should the reader care?

This section should make the paper legible before technical details appear.

### 3. Explain the core method with selective detail

Cover:
- model/backbone or system components
- training objective or optimization signal
- inference / clustering / retrieval / generation procedure
- the main design decision that differentiates it from prior work

Do not dump every symbol or equation unless the user asks.
Keep the details that explain where the gains likely come from.

### 4. Add an intuition layer

After the formal method summary, include a short interpretation section such as:
- "你可以把它想成…"
- "这篇文章的哲学是…"
- "作者其实是在挑战这样一个默认前提…"

This section is mandatory unless the user explicitly requests a purely formal style.

### 5. Interpret experiments, not just report them

When full experiments are available, include:
- datasets/tasks
- strongest or most representative comparisons
- a few concrete numbers
- what the results imply

Prefer a few representative values over copying every number.
If a baseline is stronger on one slice and weaker on another, say that explicitly.

### 6. Evaluate contribution and limitations

Separate:
- what is genuinely valuable
- what may mostly be strong engineering / scaling / recipe effects
- what remains fragile, unrealistic, or unresolved

Be fair but candid.

### 7. End with practical reading guidance

Tell the reader how to use the paper:
- worth deep reading
- worth skimming for ideas
- mainly useful as a baseline/reference/problem definition

## Evidence Rules

1. Never invent datasets, baselines, metrics, numeric gains, or conclusions.
2. Separate paper claims from your interpretation.
3. If a detail is inferred rather than directly stated, signal that clearly.
4. If only the abstract is available, do not pretend to know ablations or exact recipes.
5. Prefer representative numbers over exhaustive table transcription.

## Good Output Characteristics

A strong output should:
- make the reader feel "我知道这篇论文到底在干嘛了"
- preserve the key technical choice
- include at least one concrete result or comparison when available
- include at least one meaningful criticism
- sound like a careful researcher, not marketing copy

## Lightweight Adaptations

If the paper is a:
- benchmark/dataset paper: emphasize task definition, benchmark realism, evaluation design, and gaming risk
- methods paper: emphasize novelty, mechanism, and ablations
- review/survey: emphasize taxonomy, synthesis value, and blind spots
- medical AI paper: emphasize clinical relevance, supervision realism, validation, and deployment assumptions
- LLM/agent paper: emphasize whether gains come from the core method, tools, prompts, or compute

## Optional Closing

If useful, end with one short verdict:
- 值得精读
- 值得略读
- 适合作为思路参考
- 目前说服力一般
