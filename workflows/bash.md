# AI-Bash Workflow

[Back to library](../README.md) · [Prompts](../prompts/ai-prompt-bash.txt) · [Templates](../templates/README.md)

## Purpose
Guided path for building Bash/POSIX shell utilities with AI support, optimized for quick problem-solving on macOS with Linux targets.

## Quick Start Checklist
- Capture the problem, expected inputs/outputs, and target environments (macOS default Bash vs. `bash` 5.x).
- Initialize git repo with `bin/` or `scripts/` directory, `README`, and `.editorconfig`.
- Add `shellcheck`, `shfmt`, and basic test harness (`bats-core` or custom script).
- Record initial AI prompt context in project notes.
- Review the [project kickoff checklist](../templates/project-kickoff-checklist.md) for any gaps before prompting.

## AI Pairing Ritual
- Provide AI with desired CLI contract, sample inputs, and OS constraints.
- Request drafts for scripts + comments explaining non-obvious logic.
- Ask for alternative implementations (pure POSIX vs. Bashisms) when portability matters.
- After each session, note accepted snippets and manual tweaks.

## Development Workflow
1. **Frame & Scope**
   - Define command usage, flags, environment variables, and side effects.
   - Decide on dependencies (coreutils vs. GNU variants) and document assumptions.
   - Identify risky operations (file writes, deletes) and plan safeguards.
2. **Scaffold**
   - Create script template with `set -euo pipefail`, helper functions, and usage block.
   - Add logging helpers (`log_info`, `log_warn`) and color handling with fallbacks.
   - Configure `Makefile`/`justfile` tasks for lint, format, test, package.
3. **Implement Thin Slices**
   - Develop functions sequentially; test manually with sample data.
   - Use AI to suggest edge cases and error handling patterns.
   - Keep functions small; leverage here-docs/templates for multi-line output.
4. **Hardening**
   - Run `shellcheck` + `shfmt`; resolve portability warnings.
   - Validate on macOS (`/bin/bash` or brewed Bash) and Linux container/VM.
   - Review scripts for quoting, globbing, and IFS safety.
5. **Release & Iterate**
   - Document usage examples (`README` + `--help`).
   - Package as tarball, Homebrew formula, or simple install script.
   - Maintain changelog; track user feedback/issues.

## Testing Strategy
- Unit-style tests via `bats-core` or custom runner invoking functions with mocks.
- Integration smoke tests using Docker/CI to run script end-to-end.
- Static analysis: `shellcheck`; formatting via `shfmt`.
- Performance checks for long-running scripts (use `time`, `hyperfine`).

## Tooling
- Editor support: VS Code shell extensions, JetBrains BashSupport.
- Version control hooks: pre-commit with `shellcheck`, `shfmt`.
- Environment parity: Docker image with target Bash version; optional Nix shell.

## Deployment Options
- Simple `curl | bash` installer with checksum verification.
- Homebrew formula (`brew tap`) for macOS users.
- Linux packages or standalone script distribution with install instructions.

## Safety & Secrets
- Use `.env` files or keychain for secrets; ensure scripts fail gracefully if unset.
- Add `--dry-run` flag for destructive operations.
- Include confirmation prompts for irreversible actions.

## Open Source Checklist (Optional)
- Add `LICENSE`, `CONTRIBUTING`, issue template, and example prompts.
- Include compatibility matrix (Bash versions, macOS/Linux distros).
- Document how to run tests/lints so contributors + AI agents can reproduce.

## Retrospective Prompts
- "Were there any portability issues the AI missed?"
- "Which guardrails prevented errors during testing?"
- "What automation should I add next time (formatting, release packaging)?"
