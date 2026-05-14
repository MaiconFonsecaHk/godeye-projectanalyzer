# GodEye Project Analyzer

[Português do Brasil](README.pt-BR.md)

GodEye Project Analyzer is a structured prompt workflow for using Codex more safely, rigorously, and context-aware when analyzing and working on software projects.

It is not a single magic audit prompt. It is a step-by-step process that helps Codex:

1. read global execution preferences;
2. understand and summarize the target project;
3. create a practical smoke test plan;
4. run a deep "God Eye" project audit;
5. help the user fix issues later, by priority, without changing everything blindly.

The goal is to reduce premature implementation, lost context, unsafe assumptions, and unprioritized fixes during AI-assisted software work.

## Repository Contents

This repository includes two versions of the same workflow:

- `godeye-ptbr/` — prompts in Brazilian Portuguese.
- `godeye-en/` — prompts in English.

Choose one language per project or session to avoid mixed-language documentation. Other languages may be added in the future.

```txt
godeye-projectanalyzer/
├─ godeye-ptbr/
│  ├─ 1_user_preferences.md
│  ├─ 2_codex_resumo_do_projeto.txt
│  ├─ 3_codex_smoke_test.txt
│  └─ 4_codex_project_analyzer.txt
├─ godeye-en/
│  ├─ 1_user_preferences_en.md
│  ├─ 2_codex_project_summary.txt
│  ├─ 3_codex_smoke_test.txt
│  └─ 4_codex_project_analyzer.txt
├─ README.md
└─ README.pt-BR.md
```

## Why Use This?

Long AI coding sessions can fail in predictable ways. An assistant may:

- start coding before understanding the project;
- lose context over time;
- assume business rules that were never stated;
- mix analysis with implementation;
- fix symptoms instead of root causes;
- introduce regressions while trying to help.

GodEye reduces those risks by enforcing a slower, clearer workflow:

1. define execution rules;
2. create a factual technical summary;
3. create a smoke test checklist;
4. run a deep audit only when needed;
5. fix issues in controlled batches.

## Recommended Workflow

Use the files in numerical order:

```txt
1_user_preferences
        ↓
2_project_summary / 2_resumo_do_projeto
        ↓
3_smoke_test
        ↓
4_project_analyzer
        ↓
P0 fixes
        ↓
smoke test + tests + build
        ↓
P1 fixes
        ↓
final validation
```

## What Each File Does

### `1_user_preferences...`

Defines global behavior rules for Codex, including scope control, risk awareness, validation, asking questions when confidence is low, avoiding dangerous changes, and not inventing files, commands, or test results.

Use it at the beginning of a session or as the user's project-level execution preferences.

### `2_project_summary...`

Asks Codex to inspect the target project and create a neutral, factual technical summary.

This step is not an audit. It should not suggest improvements, classify quality, fix problems, or create a roadmap. Its purpose is to document the current state of the project so future sessions can continue with better context.

### `3_smoke_test...`

Asks Codex to create a quick validation checklist for the target project.

The smoke test should help verify that the project still installs, runs, builds, opens correctly, and keeps its main flows working after changes.

### `4_project_analyzer...`

Runs the deep "God Eye" audit.

This prompt asks Codex to look for bugs, hidden risks, technical debt, UX issues, performance bottlenecks, security and privacy risks, test gaps, data inconsistencies, build/release problems, and product risks.

The audit is diagnostic by default: it should report findings and priorities, not apply fixes automatically.

## Priority Levels

### P0 — Fix immediately

Critical issues such as crashes, data loss, serious security or privacy risks, broken builds, unusable main flows, severe user-facing text problems, or critical incorrect data.

### P1 — Fix before beta/release

Important functional bugs, confusing UX in core flows, fragile persistence, poorly handled permissions, data inconsistencies, performance risks in important screens, or missing critical tests.

### P2 — Important improvements

Relevant technical debt, maintainability issues, duplicated logic, additional test coverage, organization improvements, visual consistency, and preventive performance work.

### P3 — Future/polish

Optional refinements, product ideas, visual polish, experience improvements, and items that can wait.

## How to Use

1. Choose a language: `godeye-en/` or `godeye-ptbr/`.
2. Open the target project in Codex.
3. Send or apply the `1_user_preferences...` file.
4. Run the `2_project_summary...` prompt.
5. Review the generated summary before continuing.
6. Run the `3_smoke_test...` prompt.
7. Run the `4_project_analyzer...` prompt only when you want a deep audit.
8. Fix issues in batches: P0 first, then P1, then P2/P3.
9. Run the smoke test, relevant tests, and build after each important batch of changes.

## Example Target Project Output

When used inside another project, the workflow may create files like:

```txt
target-project/
├─ user_preferences.md
├─ myapp_summary.md
├─ myapp_smoke_test.md
├─ src/
├─ tests/
└─ README.md
```

For the Brazilian Portuguese workflow:

```txt
projeto-alvo/
├─ user_preferences.md
├─ meuapp_resumo.md
├─ meuapp_smoke_test.md
├─ src/
├─ tests/
└─ README.md
```

## Starter Prompts

English:

```txt
Use the GodEye workflow in this project.
First, read and follow the global preferences.
Do not change any files yet.
Wait for my next prompt.
```

Brazilian Portuguese:

```txt
Vou usar o fluxo GodEye neste projeto.
Primeiro, leia e siga as preferências globais.
Não altere nenhum arquivo ainda.
Aguarde meu próximo prompt.
```

Safe audit request:

```txt
Run the GodEye audit in this project.
Do not change files.
Do not refactor.
Do not commit.
Only deliver the prioritized P0/P1/P2/P3 audit report.
```

## When to Use

GodEye is useful before:

- closed beta;
- public release;
- large refactors;
- architecture changes;
- store publishing;
- monetization;
- security review preparation;
- legacy project maintenance;
- returning to a project after a long pause;
- handing a project to another person or team.

## Limitations

GodEye is an aid for analysis, documentation, and prioritization. It does not replace:

- real QA;
- human code review;
- professional security audits;
- real device testing;
- automated tests;
- manual product validation.

It does not guarantee that a project has no bugs. The quality of the analysis depends on the files available, the context provided to Codex, the model's ability to inspect the project, and the validations that are actually run.

Use the reports as decision support, not as absolute proof of quality or safety.

## License

You may use, modify, and adapt these prompts for your own projects.
