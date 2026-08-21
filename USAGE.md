# How to Use This System

Open Claude Code in this directory — `CLAUDE.md` loads the orchestration rules automatically.

## Quick Start

| Task | Command |
|------|---------|
| Create a new contract | `/new-contract [describe what you need]` |
| Review a contract you received | `/review-contract [path or paste it]` |
| Challenge one clause | "Use the challenge-reviewer agent on this clause: ..." |
| Stress-test a contract | "Use the scenario-tester agent on [path]" |

Plain requests work too — "I need an NDA for a manufacturer" routes to the generation workflow on its own.

## What Happens in Each Workflow

**Creating (`/new-contract`):** guided intake questions → you confirm the summary → drafter subagent writes the contract → challenge-reviewer subagent finds issues → revisions → scenario-tester subagent stress-tests → final contract + risk report in `output/`.

**Reviewing (`/review-contract`):** questions about your situation and leverage → full adversarial review of the document → scenarios prioritized by your concerns → prioritized issues with specific redline language, fallback positions, and negotiation talking points.

## Setting Up Your Business Context

Fill in `my-business/` once and every contract gets faster and more consistent — see `my-business/README.md` for the folder layout (company profile, default terms, deal-breakers, templates, past contracts). This folder is gitignored; real business data stays local.

## Customizing

| To change... | Edit |
|--------------|------|
| Intake questions | `.claude/commands/*.md` |
| Drafting style / boilerplate | `.claude/agents/contract-drafter.md` |
| Review rubric | `.claude/agents/challenge-reviewer.md` |
| Test scenarios | `scenarios/scenario-library.md` |
| Risk thresholds | `flows/risk-scoring.md` |
| Workflow rules | `CLAUDE.md` |

## Limitations

- Templates and analysis, not legal advice
- Always have a licensed attorney review important contracts
- State-specific laws may require modifications
- Complex transactions need human legal expertise
