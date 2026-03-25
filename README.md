# analyze-new-repo

`analyze-new-repo` is a repository analysis skill designed to help a developer understand an unfamiliar codebase quickly, without producing an overly long report.

The skill aims to produce a short, readable analysis report rather than a lightweight summary. Instead of listing files mechanically, it is designed to explain the repository's purpose, execution model, defining design decisions, visible quality signals, and practical risks using concrete evidence from the codebase.

## What This Project Provides

This repository currently provides one skill:

- `analyze-new-repo`: a skill for analyzing an unfamiliar repository and helping a developer quickly understand
  - what the project is really trying to do
  - how it runs and how it is organized
  - which design decisions define the structure
  - which risks and unknowns matter most
  - where the architectural center of gravity really is

## Intended Output Style

This skill is designed to produce:

- a report a developer can read in one pass
- analysis with judgment, not just README paraphrase
- bullet-driven output that combines facts and interpretation
- flexible sections that fit the shape of the repository

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
