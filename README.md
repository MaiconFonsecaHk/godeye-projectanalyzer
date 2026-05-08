# God Eye Project Analyzer

A powerful audit prompt for Codex designed to analyze an entire software project with the rigor of a full QA, architecture, UX, security, performance and product team.

The goal is simple: make Codex inspect a codebase deeply, find hidden risks, classify issues by priority and generate a detailed, actionable report before any code changes are made.

## What it does

This prompt asks Codex to perform a complete project audit, covering areas such as:

- Functional bugs
- Data inconsistencies
- UI/UX problems
- Performance bottlenecks
- Architecture issues
- Security and privacy risks
- Internationalization problems
- Encoding/mojibake errors
- Build and release risks
- Testing gaps
- Technical debt
- Product and monetization risks

It is designed to work as a general-purpose review prompt for any software project.

## Main idea

Instead of asking Codex to immediately fix code, this prompt forces it to first act like a full review team:

- Manual QA
- Automated QA
- Senior software engineer
- Software architect
- UX/UI specialist
- Security reviewer
- Performance engineer
- Product reviewer
- Beta tester

Codex must analyze the project, identify risks, cite files and lines when possible, classify findings by severity and suggest a correction plan.

## Priority system

The report must classify issues as:

### P0 — Fix immediately

Critical issues such as crashes, data loss, serious security problems, broken user-facing text, wrong critical data or broken main flows.

### P1 — Fix before beta/release

Important functional bugs, inconsistent data, confusing UX, fragile persistence, permissions problems or performance risks in important screens.

### P2 — Important improvements

Technical debt, maintainability improvements, preventive performance fixes, missing tests and consistency improvements.

### P3 — Future/polish

Optional improvements, product ideas, visual refinements and future enhancements.

## How to use

1. Open your project in Codex.
2. Paste the prompt from this repository.
3. Tell Codex to run only the audit.
4. Do not allow changes before reviewing the report.
5. After the report, choose which priorities should be fixed first.

Recommended short instruction before using:

> Do not change any files. Run only the audit and deliver the full report.

## Important behavior

The prompt explicitly tells Codex to:

- Not modify files
- Not refactor
- Not commit changes
- Not apply fixes automatically
- Separate certainty from hypothesis
- Separate bugs from product decisions
- Separate immediate risks from future technical debt
- Provide an actionable correction plan

## Suggested workflow

1. Run God Eye Project Analyzer.
2. Read the report.
3. Approve only the first correction batch.
4. Fix P0 issues.
5. Re-run tests/build.
6. Commit.
7. Continue with P1/P2 items.

## Why use this?

Because many AI coding sessions jump directly into implementation without fully understanding the project.

This prompt helps prevent:

- Wrong assumptions
- Hidden regressions
- Unsafe refactors
- Poorly prioritized fixes
- Superficial reviews
- Ignored edge cases
- Incomplete QA

It is especially useful before:

- Beta releases
- Public releases
- Large refactors
- Monetization
- Store publishing
- Major feature development
- Long-term maintenance planning

## Repository contents

This repository contains a reusable prompt for deep project audits.

Suggested files:

- `GodEye_ProjectAnalyzer.txt`
- `README.md`

## Example use cases

Use this prompt when you want Codex to answer questions like:

- Is this project ready for beta?
- What can break with real users?
- Where are the hidden risks?
- What should be fixed first?
- Are the metrics/data reliable?
- Is the architecture scalable?
- Are there performance problems?
- Are there user-facing text or encoding bugs?
- What tests are missing?
- What could hurt user trust?

## License

You can use, modify and adapt this prompt for your own projects.
