# AI-Go Workflow

[Back to library](../README.md) · [Prompts](../prompts/ai-prompt-go.txt) · [Templates](../templates/README.md)

## Purpose
Solo workflow for building Go-based CLIs and services with AI help, optimized for macOS development targeting macOS/Linux binaries.

## Quick Start Checklist
- Clarify the problem, target audience, success metric, and release deadline.
- Initialize module with `go mod init`, set Go version, and choose package layout (`cmd/`, `internal/`).
- Configure task runner (`make`, `mage`, or `just`) with build, test, lint targets.
- Record initial requirements + AI prompt context in project notes.
- Walk through the [project kickoff checklist](../templates/project-kickoff-checklist.md) to capture constraints and risks.

## AI Pairing Ritual
- Pre-session brief: share current stage, desired output, constraints (binary size, concurrency, etc.).
- Request plans → review → ask for focused snippets (structs, goroutines, tests) → integrate manually.
- After each session, log accepted code, rationales, and TODOs so the context survives.

## Development Workflow
1. **Frame & Design**
   - Model CLI command tree or API surface; decide on libraries (`cobra`, `urfave/cli`, standard `flag`).
   - Note concurrency, performance, or cross-compilation needs.
   - Capture go/no-go decision and risks (e.g., CGO, external APIs).
2. **Scaffold**
   - Generate `cmd/<app>/main.go`, internal packages, and configuration structs.
   - Add tooling: `golangci-lint`, `staticcheck`, `go test`, `gofmt`, `goimports`.
   - Set up `.editorconfig`, `pre-commit`, and GitHub Actions pipeline (test + build matrix).
3. **Implement Thin Slices**
   - Build features incrementally; keep packages cohesive and interfaces small.
   - Use AI to brainstorm struct designs, interfaces, and error handling strategies.
   - Write table-driven tests alongside code; run `go test ./...` frequently.
4. **Hardening**
   - Optimize performance (profiling with `pprof`, benchmarking via `go test -bench`).
   - Ensure graceful shutdowns (contexts, signals), logging, and metrics.
   - Validate cross-compilation (`GOOS`, `GOARCH`) and binary size.
5. **Release & Iterate**
   - Produce `--help` output, README quickstart, and sample configs.
   - Tag releases, generate changelog, and create reproducible builds (`goreleaser`, `nfpm`).
   - Track issues/backlog; schedule follow-up AI sessions for enhancements.

## Testing Strategy
- Unit + integration tests via `go test ./...` with coverage.
- CLI smoke tests using `go test` + `exec.Command` or `github.com/Netflix/go-expect`.
- Static analysis: `golangci-lint`, `staticcheck`, `govulncheck`.
- Cross-platform CI builds for macOS and Linux (optionally Windows).

## Tooling
- Version management: `asdf` or Go toolchain (`asdf global go`, `gvm`).
- Task automation: `make`, `just`, `mage`, or `Taskfile.yml`.
- Debugging: `delve`, `pprof`, `richgo` for improved output.
- Observability: structured logging (`zap`, `zerolog`), metrics via `prometheus` client.

## Packaging & Distribution
- Use `goreleaser` for multi-platform binaries, archives, checksums, Homebrew taps.
- Provide install options: `go install`, Homebrew, Linux packages (deb/rpm), Docker images.
- Sign binaries (cosign, minisign) and publish SBOMs when appropriate.

## Data & Config
- Store secrets in macOS Keychain, 1Password CLI, or `.env` encrypted files.
- Support config files (YAML/JSON/TOML) and env var overrides; document precedence.
- Handle local caches/state under XDG directories (macOS `~/Library/Application Support`).

## Open Source Readiness (Optional)
- Include `LICENSE`, `CONTRIBUTING.md`, issue/PR templates.
- Provide Makefile targets that run all tests/lints for contributors + AI agents.
- Add `CODEOWNERS` and security policy (SECURITY.md) if accepting disclosures.

## Retrospective Prompts
- "Which parts of the codebase benefited most from AI assistance?"
- "Did cross-compilation or tooling cause surprises?"
- "What automation should I add before the next release?"
