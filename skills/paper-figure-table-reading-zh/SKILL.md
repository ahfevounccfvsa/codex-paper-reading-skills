---
name: paper-figure-table-reading-zh
description: Interpret figures, tables, algorithms, diagrams, and ablation plots from research papers in Chinese with self-contained local explanations of labels, jargon, abbreviations, and ambiguous terms. Use when the user asks for paper figure/table reading, "图表解读", "figures/tables explanation", visual evidence-chain analysis, pros/cons or strengths/limitations of paper evidence, or wants to understand what each figure/table proves without needing to reopen the original paper for unclear wording.
---

# Paper Figure/Table Reading Zh

## Goal

Turn a paper's figures, tables, algorithms, diagrams, and captions into a high-signal Chinese reading brief that works as a companion to a separate paper explanation. Do not re-explain the whole paper unless the user asks. Instead, make each figure/table locally understandable: translate or define confusing labels, jargon, abbreviations, English phrases, metrics, and workflow terms the first time they appear.

## Source Discipline

Use the paper itself as the primary source. Prefer, in order:

1. Local PDF or extracted full text supplied by the user.
2. Official paper page, publisher page, arXiv/OpenReview/PMC page, or project repository.
3. Secondary pages only for locating the primary source, not for interpreting results.

If the user names only a title, identify the exact paper before interpreting. If the paper is recent, niche, or specific, browse or inspect the local PDF rather than relying on memory. Include source links in the final answer when web sources were used.

Do not invent missing figures, table numbers, metrics, datasets, or conclusions. If a figure/table is inaccessible, say so and interpret only from available captions/text.

## Reading Workflow

1. Identify bibliographic context: title, version/year, venue if visible, and the paper's main claim.
2. Add only minimal context needed for the figures/tables: the task, method name, evaluation object, and any metric definitions required to read the visuals.
3. Build an inventory of all visual evidence: figures, tables, algorithms, appendices if relevant.
4. Read each caption plus the nearby paragraphs that reference it. For tables, read column definitions and metric meanings.
5. Explain each item by function, not by literal translation. If the caption or figure uses terms like "pros/cons analysis", "ablation", "baseline", "ASR", "F1", "prompt leaking", or "semantic strategy", keep the original term when useful but immediately add a Chinese explanation at the point of use.
6. Connect items into a chain: motivation/threat model, method, experimental setup, main results, ablations, limitations.
7. Add critical reading: evidence strengths, evidence weaknesses, reproducibility, metric ambiguity, sample size, dataset/app anonymity, baseline choice, temporal drift, or mismatch with the user's use case.

## Output Structure

Use Chinese. Keep the answer readable and direct.

Start with:

- **最小上下文**: 2-4 sentences explaining only what is needed to read the figures/tables, assuming the user may already have a separate paper summary.
- **一句话总读法**: what the paper's figures/tables collectively prove.
- **图表证据链**: 2-5 bullets summarizing how the visuals move from problem to evidence.
- **Pros/Cons Analysis（利弊分析/优缺点分析）**: explain this label the first time as "分别看支持理由、反对理由和关键权衡点"; then describe what the figures/tables prove well, what they only weakly support, and what they cannot prove.

Then cover items in order:

```markdown
**Figure 1: [short Chinese title]**
它在讲什么:
[one or two sentences]

你应该看哪里:
[specific axes, panels, arrows, counts, conditions, or comparison]

容易卡住的词:
[define confusing labels, abbreviations, metrics, or English phrases that appear in this item; omit only if truly unnecessary]

它支撑了什么结论:
[the paper-level claim this visual supports]

读的时候要小心:
[caveat, hidden assumption, or possible overclaim]
```

For tables:

```markdown
**Table 1: [short Chinese title]**
这张表的作用:
[what the rows/columns compare]

最关键的数字/模式:
[specific values or ranking if available]

它真正说明:
[interpretation beyond reading numbers aloud]

局限:
[what the table cannot prove]
```

For algorithms/framework diagrams, replace numeric interpretation with workflow interpretation:

- input/output
- components or stages
- where feedback, supervision, or attack/defense assumptions enter
- what would break if an assumption changes

## Style Rules

- Explain like an experienced paper reader talking to a collaborator, not like a caption translator.
- Assume the user may have read your separate paper explanation but has not memorized the original paper's labels. Do not repeat the whole paper summary; explain only the local context needed to understand each figure/table.
- Prefer "这张图/表的作用是..." over vague praise.
- When numbers are central, quote the exact numbers; when the visual is conceptual, explain the conceptual role.
- Separate "作者声称" from "图表实际支持".
- Do not leave unexplained English abstractions. When using "pros/cons analysis", write it as "Pros/Cons Analysis（利弊分析/优缺点分析：分别看支持理由、反对理由和关键权衡点）" on first use. In concrete examples, spell out the meaning directly, such as "支持读 PhD 的理由有哪些、不支持的理由有哪些、最后怎么权衡".
- Any term likely to make the user ask "这是什么意思?" should be explained inline the first time it appears.
- If there are many appendix figures/tables, prioritize main-text figures/tables first and summarize appendices by theme unless the user asks for exhaustive coverage.
- If the user is applying the paper to their own project, add a short "对你们项目的启发/警惕" section.

## Quality Checklist

Before finalizing, verify:

- All figure/table numbers mentioned exist in the source.
- No table metric is interpreted without knowing whether higher/lower is better.
- Ablations are not described as main results.
- Conceptual diagrams are tied to the paper's assumptions.
- The final answer explains why each item matters, not just what it contains.
- No unexplained phrase, metric, acronym, or English label remains when it is necessary for understanding a figure/table.
- The figure/table explanation is understandable after reading the separate paper brief, without forcing the user to reopen the original paper just to decode terminology.
