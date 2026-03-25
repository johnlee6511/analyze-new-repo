# analyze-new-repo

`analyze-new-repo` is a repository analysis skill for developers opening an unfamiliar codebase for the first time.

It is designed to produce a short, readable analysis report that helps a developer understand the repository's purpose, execution model, defining design decisions, architectural center of gravity, and practical risks without turning the result into an overly long walkthrough.

## What This Project Provides

This repository currently provides one skill:

- `analyze-new-repo`
  - explains what the project is really trying to do
  - explains how it runs and how it is organized
  - surfaces the design decisions that define the codebase
  - highlights the most important risks and unknowns
  - identifies where the repository's real structural weight sits

## Intended Output Style

The skill is designed to produce:

- a report a developer can read in one pass
- analysis with judgment, not just README paraphrase
- bullet-driven writing that combines facts and interpretation
- section structure that adapts to the repository instead of forcing one rigid template

The goal is to help a developer form the right mental model quickly after opening a new repository.

## Installation

Install directly from GitHub:

```bash
npx skills add johnlee6511/analyze-new-repo
```

Install only this skill:

```bash
npx skills add johnlee6511/analyze-new-repo --skill analyze-new-repo
```

Install for a specific agent:

```bash
npx skills add johnlee6511/analyze-new-repo -a claude-code
npx skills add johnlee6511/analyze-new-repo -a codex
npx skills add johnlee6511/analyze-new-repo -a opencode
npx skills add johnlee6511/analyze-new-repo -a pi
```

You can also install from the full GitHub URL:

```bash
npx skills add https://github.com/johnlee6511/analyze-new-repo
```

## Repository Layout

```text
skills/
  analyze-new-repo/
    SKILL.md
    references/
      checklist.md
      report-template.md
examples/
  karpathy-autoresearch.md
LICENSE
README.md
```

## Key Files

- `skills/analyze-new-repo/SKILL.md`
  - The main skill definition. It contains the investigation workflow, output rules, evidence rules, and writing quality bar.
- `skills/analyze-new-repo/references/checklist.md`
  - A compact checklist for repository analysis.
- `skills/analyze-new-repo/references/report-template.md`
  - A structure guide for the final report.
- `examples/karpathy-autoresearch.md`
  - A sample output for a small, distinctive repository. It is an example of the intended tone and synthesis level, not a universal template.

## Development and Local Checks

List skills discovered from the current directory:

```bash
npx skills add . --list
```

Test installing this skill from a local checkout:

```bash
npx skills add . --skill analyze-new-repo -a claude-code
```

## License

MIT License. See `LICENSE` for details.
