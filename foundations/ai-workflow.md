# AI Workflow

[Back to library](../README.md) · [Language Playbooks](../workflows) · [Prompt Templates](../prompts) · [Reusable Checklists](../templates/README.md)

## Purpose
Serve as my solo-builder roadmap when pairing with AI to plan, build, and operate small apps quickly, while leaving just enough traceability to share or open-source later.

## Related Workflows
- `workflows/python-cli.md`
- `workflows/bash.md`
- `workflows/zsh.md`
- `workflows/go-cli.md`
- Prompt kickoffs: `prompts/ai-prompt-python.txt`, `prompts/ai-prompt-bash.txt`, `prompts/ai-prompt-zsh.txt`, `prompts/ai-prompt-go.txt`

## Guiding Principles
- Anchor every build on the concrete problem and outcome I need, not the model or API I want to try.
- Keep myself in the loop: schedule quick review gates where judgement, safety, or risk trade-offs matter.
- Document decisions lightly so "future me" or potential open-source users can follow the thread; capture them in `docs/ai-sessions.md` after each working block.
- Treat data as a product: track lineage, ownership, and quality expectations even for personal datasets.
- Ship in thin slices so I can validate, learn, and iterate with minimal sunk cost.

## Hats I'm Wearing
- **Product Hat** – frame the user problem, success metrics, and any constraints (time, cost, privacy).
- **Data / ML Hat** – scout datasets, shape prompts or models, and evaluate quality and feasibility.
- **Engineering Hat** – wire integrations, handle deployment, and make sure ops are sustainable.
- **Design / Research Hat** – validate that the UX (CLI, UI, docs) solves the pain and stays usable.
- **Compliance / Risk Hat** – spot legal, ethical, or privacy concerns before sharing or open-sourcing.

## Workflow Stages

### 1. Frame the Opportunity
- Align on the user problem, target outcomes, and constraints.
- Draft an AI Canvas: users, key tasks, success metrics, failure modes, and acceptable risk levels.
- Capture a quick opportunity note (one-pager or Kanban card) so the scope stays focused.
- Solo gate: decide go/no-go based on impact, feasibility, and risk; log the decision.

### 2. Audit and Prepare Data
- Inventory available data sources, ownership, and governance.
- Assess data quality and identify gaps; create a remediation plan if needed.
- Define labeling strategy (automated vs. human) and annotation guidelines.
- Keep lightweight documentation: data dictionary stubs, privacy notes, retention expectations.

### 3. Prototype and Validate Approach
- Select baseline models or APIs; outline experiment matrix.
- Build thin vertical slice in a sandbox; instrument for evaluation.
- Collect offline metrics (precision, recall, latency, cost) and qualitative feedback.
- Run red-teaming / adversarial checks for safety and bias.
- Solo gate: decide whether to iterate, pivot, or halt, and capture why for future reference.

### 4. Hardening for Production
- Choose deployment architecture (batch, real-time, human-in-the-loop).
- Implement feature pipelines, prompt templates, or model serving endpoints.
- Add guardrails: validation rules, fallback logic, observability hooks.
- Document personal runbooks, escalation paths, and rollback procedures (even if it's just a checklist).
- Solo gate: run a self-review checklist (risk, compliance, support) before wider release or sharing.
- Reference the [release readiness checklist](../templates/release-readiness-checklist.md) to confirm coverage.

### 5. Launch and Learn
- Release to controlled audience; monitor success metrics and user feedback.
- Track model/data drift, latency, cost, and incident tickets.
- Schedule model/data refresh cadence and continuous evaluation tasks.
- Feed learnings back into backlog; prioritize automation and tooling improvements.
- Note any changes needed before publishing as open source (licensing, docs, security review).

## Artifacts Checklist
Use these as lightweight checklists; capture only what's needed to rebuild context later.
- AI Canvas (problem framing, metrics, risks)
- Data inventory + governance notes
- Experiment log with metrics and decisions
- Technical design + integration diagrams
- Runbook with on-call, rollback, and audit details
- Publishing prep: LICENSE choice, README template, contribution notes

## Stakeholder Snapshot (Optional)
Use when looping in collaborators or preparing to open-source; otherwise, treat each stage as a reminder of the hat you're wearing.
| Stage | What I Own | Who to Loop In |
| --- | --- | --- |
| Frame Opportunity | Problem framing, success metrics | Potential users, mentors |
| Data Prep | Data sourcing, privacy check | Data owners (if external), legal templates |
| Prototype | Experiments, evaluation | Trusted testers for feedback |
| Production Hardening | Deployment, guardrails, ops | Security reviewers, platform teams |
| Launch & Learn | Release notes, iteration plan | Community/users once shared |

## Operational Cadence
- Daily (5 min): capture progress, blockers, and the next AI prompt you'll need.
- Weekly (30 min): review metrics, debt, and release readiness; adjust backlog.
- Monthly (60 min): run a personal retro, tidy docs, and plan any open-source drops.

## Tailoring the Workflow
- When working solo, collapse meetings into personal check-ins but keep written decisions.
- Scale down stages for low-risk experiments (e.g., internal tooling, low data sensitivity).
- Add parallel compliance/security tracks when dealing with regulated data.
- Tie into existing SDLC artifacts (PRDs, architecture reviews, change management) to avoid duplication.

## Working with an AI Partner
- Use this document to prime AI sessions: share the current stage, desired outcome, and constraints in each prompt.
- Capture AI-generated plans or code snippets in your repo/issues so you can trace decisions later.
- After each stage, summarize what the AI delivered, what you accepted, and any follow-up questions.
- Periodically review prompt hygiene (context provided, instructions, checks) to keep outputs reliable.
- Close each session using `ai-prompt-session-recap.txt` and append the summary to `docs/ai-sessions.md`.
- Before starting a slice, fill out the [thin slice plan template](../templates/thin-slice-plan-template.md) so prompts stay focused.

## CLI Development Workflow (High Level)
- **Frame the tool**: Capture the command-line experience you want, primary use cases, required flags/subcommands, and cross-platform behaviors.
- **Set up environments**: Use macOS as the primary dev host with version managers (`pyenv`, `asdf`, `nvm`) and reproducible shells (`direnv`, `.envrc`). Define how you will mirror Linux targets (containers, VMs, CI runners).
- **Scaffold projects**: Standardize repo structures, licensing, and bootstrapping scripts for Bash/Zsh/Python so new tools start consistent. Include lint/test configs and lightweight task runners.
- **Develop iteratively**: Implement features in thin slices, favor small, composable scripts or modules. Pair IDEs (VS Code, PyCharm) with terminal workflows, keep scripts POSIX-friendly unless macOS-only. Add comments/tests only where behavior is non-obvious.
- **Validate portability**: Run unit/integration tests in macOS and Linux shells. Use CI to enforce style, type checks (e.g., `ruff`, `shellcheck`), and smoke-test packaged binaries or wheels.
- **Package & release**: Provide install paths (`brew`, `pipx`, tarballs) and versioned changelog entries. Automate builds so artifacts are reproducible and signed when needed.
- **Document & support**: Maintain README usage examples, command reference, and troubleshooting notes. Track issues, gather user feedback, and schedule periodic dependency/security reviews.
- **Open-source (optional)**: Prep licensing, contributor guidelines, and lightweight community policies before publishing.

## Success Signals
- I can restate the problem, target users, and risk profile without rereading specs.
- My notes and repos make sense when I return weeks later or invite collaborators.
- I measure impact versus manual baselines (time saved, accuracy, cost) before scaling.
- Operations are sustainable: ownership is clear (me), costs are predictable, performance is monitored.
