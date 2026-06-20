# Codex Paper Reading Skills

Four Chinese paper-reading skills for Codex-style research workflows.

These skills are designed for researchers who want paper explanations that are concrete, evidence-aware, and useful for real reading, not just abstract summaries.

## Included Skills

- `paper-reading`: general Chinese paper speed-reading notes for abstracts, extracted full text, or paper notes.
- `paper-speedread-zh`: a higher-density "论文速读" style with intuition, key details, representative results, and critical reading.
- `paper-results-chain-zh`: experiment/result-chain explanations centered on data, metrics, figures, author interpretation, and caveats.
- `paper-figure-table-reading-zh`: figure, table, algorithm, and ablation walkthroughs that explain what each visual actually supports.

## Installation

Copy the skill directories into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R skills/paper-reading ~/.codex/skills/
cp -R skills/paper-speedread-zh ~/.codex/skills/
cp -R skills/paper-results-chain-zh ~/.codex/skills/
cp -R skills/paper-figure-table-reading-zh ~/.codex/skills/
```

Restart Codex after copying the files so the skills can be discovered.

## Usage Examples

Ask Codex in Chinese, for example:

```text
用 paper-reading 帮我解读这篇论文。
```

```text
用 paper-speedread-zh 做一版论文速读，重点讲清楚方法和实验结果。
```

```text
用 paper-results-chain-zh 讲这篇文章的实验结果链条。
```

```text
用 paper-figure-table-reading-zh 帮我逐图逐表解释这篇论文。
```

## Design Principles

- Explain what the paper actually does, not only what the abstract claims.
- Separate source-supported facts from interpretation.
- Preserve important methods, datasets, metrics, and representative numbers.
- Make uncertainty explicit when only limited paper text is available.
- Include critical reading so strong claims are not accepted too easily.

## Repository Layout

```text
skills/
  paper-reading/
  paper-speedread-zh/
  paper-results-chain-zh/
  paper-figure-table-reading-zh/
```

Each skill is self-contained under its own directory. Some skills include optional `agents/openai.yaml` metadata for UI display or prompt presets.

## License

MIT License.
