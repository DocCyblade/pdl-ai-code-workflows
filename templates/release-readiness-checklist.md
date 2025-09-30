# Release Readiness Checklist

Run through this before sharing binaries/scripts or publishing open source.

## Product & UX
- [ ] Usage instructions in README and `--help`
- [ ] Example commands / screenshots verified
- [ ] Configuration options documented with defaults

## Quality
- [ ] Automated tests passing (unit, integration, smoke)
- [ ] Manual QA for critical workflows completed
- [ ] Performance / latency / cost within targets

## Compliance & Safety
- [ ] Licensing for dependencies reviewed
- [ ] Security review (secrets, sensitive data) complete
- [ ] Risk mitigations/guardrails validated (dry runs, confirmations)

## Operations
- [ ] Logging/metrics/alerts in place (if applicable)
- [ ] Rollback or disable plan documented
- [ ] Support notes or troubleshooting section added

## Packaging & Distribution
- [ ] Version bumped and tagged
- [ ] Artifacts built (binaries, wheels, tarballs) with checksums/signatures
- [ ] Release notes / changelog updated
- [ ] Distribution channels prepared (Homebrew tap, `pipx`, GitHub Release)

## Follow-Up
- [ ] Session recap logged with open questions
- [ ] Next slice or maintenance tasks captured in backlog
