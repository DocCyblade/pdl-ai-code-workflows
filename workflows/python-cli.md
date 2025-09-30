# AI-Python CLI Workflow

[Back to library](../README.md) · [Prompts](../prompts/ai-prompt-python.txt) · [Templates](../templates/README.md)

## Purpose
Solo-builder playbook for creating Python-based CLI tools with AI assistance, optimized for macOS development and Linux/macOS deployment.

## Quick Start Checklist
- Define the problem, target users (even if it's just me), success metric, and deadline.
- Spin up a fresh virtual environment via `uv`, `pipenv`, or `python -m venv`.
- Capture initial requirements + prompts in `docs/notes.md` or project tracker.
- Create a repo scaffold with task runner (`make`, `just`, or `task`), `pyproject.toml`, and lint/test configs.
- Skim the [project kickoff checklist](../templates/project-kickoff-checklist.md) to ensure context is ready for the AI session.

## AI Pairing Ritual
- **Before session**: write a short brief (problem, constraints, current stage) to paste into prompts.
- **During session**: ask for plan → review → request focused code snippets/tests → run locally.
- **After session**: log decisions, accepted snippets, follow-ups in project notes to keep context durable.

## Development Workflow
1. **Frame & Plan**
   - Outline CLI commands, flags, subcommands, and dependencies.
   - Choose core libraries (e.g., `click`, `typer`, `argparse`) and note why.
   - Model go/no-go, risks, and scope with AI-generated pros/cons captured in notes.
2. **Scaffold & Configure**
   - Use AI to draft `pyproject.toml`, entry points, and initial module layout.
   - Add tooling: `ruff`/`flake8`, `black`, `mypy` (if helpful), `pytest`, `coverage`.
   - Set up pre-commit hooks for lint/test when committing.
3. **Implement Thin Slices**
   - Iterate feature-by-feature; keep modules small and testable.
   - Pair with AI for function stubs, docstrings, and edge-case brainstorming.
   - Run unit tests often; capture failing cases for AI to analyze.
4. **Hardening**
   - Add logging, error handling, and user-facing messages consistent with CLI UX.
   - Ensure configuration options (env vars, config files) are documented.
   - Double-check dependency versions, license compatibility, and OS portability.
5. **Launch & Iterate**
   - Produce `--help` text, README usage sections, and quickstart examples.
   - Measure performance, runtime cost, and success metrics; adjust backlog.
   - Track issues in TODO list; schedule follow-up AI sessions for improvements.

## Testing Strategy
- Unit tests with `pytest`; prefer table-driven cases.
- CLI smoke tests using `pytest` + `subprocess` or `typer.testing.CliRunner`.
- Static analysis: `ruff`, `mypy` (optional), `bandit` for security.
- Cross-platform check via GitHub Actions workflow (macOS + Ubuntu runners).

## Packaging & Distribution
- Package via `pyproject.toml` + `setuptools`/`poetry`/`hatch`.
- Provide install paths: `pipx install .`, `pip install`, or Homebrew tap (via `shiv`/`pynsist` if needed).
- Generate versioned changelog, release tags, and signed artifacts if sharing widely.

## Dev Tooling
- Version management: `pyenv` or `asdf`.
- Task automation: `just` or `make` for setup/test/release commands.
- Debugging: `ipdb`, `rich` tracebacks, `loguru` for quick logging.
- Observability: add structured logging when running long tasks.

## Data & Secrets
- Store secrets in `.env` + `direnv` or macOS Keychain; never hardcode.
- For local datasets, note source, refresh cadence, and privacy considerations.

## Open Source Readiness (Optional)
- Choose license (MIT/Apache-2); include `LICENSE` file.
- Create CONTRIBUTING + issue templates with instructions for AI-generated PR review.
- Provide code of conduct and release checklist.

## Retrospective Prompts
- "What went well/struggled when building this CLI?"
- "Which prompts produced the best code/tests?"
- "What automation should I add before the next release?"
