# AI-Zsh Workflow

[Back to library](../README.md) · [Prompts](../prompts/ai-prompt-zsh.txt) · [Templates](../templates/README.md)

## Purpose
Solo workflow for building Zsh-first scripts and plugins with AI help, targeting macOS shells and optional Linux Zsh setups.

## Quick Start Checklist
- Define the user task, target shells (plain Zsh, Oh My Zsh, Prezto), and distribution method.
- Initialize repo with `zsh-scripts/` or `plugins/`, `README`, and `.zshrc` example snippets.
- Add lint/format tools (`zsh-syntax-highlighting` test harness, `zfmt` or `shfmt -ln=zsh`).
- Capture prompt context + desired plugin behaviors in notes.
- Check the [project kickoff checklist](../templates/project-kickoff-checklist.md) to confirm compatibility considerations are captured.

## AI Pairing Ritual
- Share the desired widget/binding/plugin behavior and compatibility requirements.
- Ask AI for function scaffolds, completion definitions, and prompt segment templates.
- Request translation to POSIX when fallback is needed.
- Log accepted AI output and manual adjustments for future reference.

## Development Workflow
1. **Frame & Design**
   - Specify functions, key bindings, prompt segments, and configuration options.
   - Decide support matrix (macOS default Zsh, Homebrew Zsh, Linux distros).
   - Plan for optional dependencies (fzf, ripgrep) with graceful fallbacks.
2. **Scaffold**
   - Create main script with `emulate -L zsh`, `setopt ERR_EXIT`, and helper function sections.
   - Provide install snippet (`antigen`, `zinit`, manual sourcing) in docs.
   - Configure task runner (`make`, `just`) for lint/test/demo commands.
3. **Implement Features**
   - Use AI to draft widgets, completion functions, and prompt segments.
   - Keep state isolated; prefer local scopes and `typeset` for parameters.
   - Add usage examples and self-tests for each function.
4. **Hardening**
   - Run `shellcheck -s zsh` (or `shellcheck` with allowances) and `shfmt -ln=zsh`.
   - Test in macOS Terminal/iTerm2 and Linux Zsh (Docker) with various frameworks.
   - Verify key bindings, completion behavior, and prompt rendering under different themes.
5. **Release & Iterate**
   - Document install steps for popular managers (Oh My Zsh custom plugins, Antidote, Znap).
   - Package versioned releases with changelog and demo GIF/screenshots.
   - Collect feedback; maintain backlog of enhancements + compatibility fixes.

## Testing Strategy
- Write smoke tests using `zunit` or custom harness invoking functions non-interactively.
- Use snapshot tests for prompt output (`zpty` + fixtures).
- Automated checks in CI across macOS and Ubuntu images with Zsh 5.8+ / 5.9.

## Tooling
- Editor plugins: VS Code `zsh` extension, JetBrains shell plugin.
- Pre-commit hooks running `shfmt -ln=zsh`, `shellcheck` (with Zsh sourcing).
- Demo environment: `docker run -it --rm zshusers/zsh` for clean shell testing.

## Deployment Options
- Publish to GitHub with install instructions for popular plugin managers.
- Offer Homebrew formula or `zsh -c` installer for CLI utilities.
- Provide `zplugin`/`antigen` snippet for quick sourcing.

## Safety & Compatibility
- Avoid hardcoding macOS paths; detect OS + dependencies at runtime.
- Provide fallback behaviors for missing optional tools.
- Document environment variables that influence behavior.

## Open Source Checklist (Optional)
- Include `LICENSE`, `CONTRIBUTING`, screenshots/demos, and compatibility table.
- Add automated installer tests and CI badges.
- Provide template prompts for contributors using AI assistance.

## Retrospective Prompts
- "Which shell environments were hardest to support and why?"
- "Did AI-generated completions/prompt segments behave as expected?"
- "What should I automate next to speed up testing or releases?"
