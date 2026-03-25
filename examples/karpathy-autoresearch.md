# Example: karpathy/autoresearch

This example shows the intended output style for `analyze-new-repo`.

It is not meant to be the only correct answer. It is meant to demonstrate the desired level of synthesis, section flexibility, and evidence-backed judgment on a small, distinctive repository.

## Repository Thesis

- This repository is best understood not as a generic PyTorch training repo, but as a compact harness for agent-driven model experimentation under controlled constraints (`README.md`, `program.md`). Its core design move is to freeze evaluation and data preparation in `prepare.py` while concentrating all editable research surface area in `train.py`.
- The strongest evidence is the combination of `README.md`, which frames the project as overnight autonomous research, and `program.md`, which defines an explicit keep/discard experiment loop for an agent. Together they show that the real product here is the research loop, not just the model code.

## Execution Model

- The shortest trustworthy run path is `uv sync` → `uv run prepare.py` → `uv run train.py` (`README.md`). That order matters because `prepare.py` builds the cache, tokenizer, dataloader, and evaluation prerequisites consumed by `train.py`.
- The runtime target is narrow by design: a single NVIDIA GPU with CUDA-oriented PyTorch packaging (`pyproject.toml`, `README.md`). This makes the repo easy to reason about for one hardware profile, but reduces portability.

## Distinctive Design Decisions

- The most important design constraint is the hard separation between mutable and immutable surfaces. `program.md` explicitly allows editing `train.py` while treating `prepare.py` and the evaluation harness as fixed. That preserves comparability between experiments and prevents the agent from gaming the metric.
- The fixed 5-minute wall-clock budget (`prepare.py`, `README.md`) is another defining choice. The repo is not optimizing for absolute benchmark quality; it is optimizing for how much progress an agent can make per bounded experiment cycle.

## Architectural Center of Gravity

- `prepare.py` is structurally central even though it is not the main editing target. It defines `TIME_BUDGET`, `MAX_SEQ_LEN`, `evaluate_bpb`, tokenizer behavior, and the dataloader, so it effectively locks the rules of the experiment.
- `train.py` is the only meaningful code surface the agent iterates on. Model shape, optimizer behavior, hyperparameters, and the training loop all live there, which keeps the search space legible.
- `program.md` acts like an operational control plane. It encodes branch policy, result logging, crash handling, and the autonomous loop itself.

## Quality Signals and Risks

- Documentation is unusually aligned with implementation for such a small repo: `README.md` explains the philosophy, while `program.md` turns that philosophy into operating procedure. That coherence is a strength.
- Conventional software quality signals are thin: no visible tests, CI, or contribution workflow. In this case that is less a sign of neglect than a sign that the repository is optimized for experimentation rather than reusable product development.
- The main practical risk is environmental fragility. Cache state, GPU assumptions, and external data downloads all affect first-run success, even though the happy-path instructions are short.
