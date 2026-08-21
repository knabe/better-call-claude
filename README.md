# Better Call Claude

*Multi-agent contract generation with built-in challenge testing*

A Claude Code-native system for generating, challenging, and stress-testing legal contracts for business owners.

## Language Philosophy

| What | Language Style |
|------|----------------|
| **Generated Contracts** | Professional legal language (formal, attorney-style drafting) |
| **Explanations to Users** | Plain English (accessible, jargon-free) |

Contracts are drafted with proper legal terminology, recitals, whereas clauses, and formal structure — indistinguishable from attorney-drafted agreements. All explanations, questions, and guidance are in plain English so non-lawyers understand what they're signing.

## Architecture

Interactive intake happens in the main conversation (slash commands); the heavy lifting runs as autonomous subagents with fresh context — the reviewer and tester judge the contract text on its merits, not the drafting conversation.

```
                    MAIN CONVERSATION (CLAUDE.md)
        /new-contract intake  │  /review-contract intake
                              │
        ┌─────────────────────┼─────────────────────┐
        ▼                     ▼                     ▼
┌───────────────┐    ┌─────────────────┐    ┌───────────────┐
│   CONTRACT    │───▶│    CHALLENGE    │    │   SCENARIO    │
│    DRAFTER    │◀───│    REVIEWER     │    │    TESTER     │
│  (subagent)   │    │ (fresh-context  │    │  (subagent,   │
│               │    │    subagent)    │    │ parallelizable)│
└───────┬───────┘    └─────────────────┘    └───────┬───────┘
        │                                           │
        ▼                                           ▼
┌───────────────────────────────────────────────────────────┐
│              RISK SCORING & OUTPUT (output/)              │
└───────────────────────────────────────────────────────────┘
```

## Components

| Component | File | Purpose |
|-----------|------|---------|
| Orchestration + rules | `CLAUDE.md` | Workflows, quality gates, language rules — loaded automatically |
| `/new-contract` | `.claude/commands/new-contract.md` | Interactive intake → full generation pipeline |
| `/review-contract` | `.claude/commands/review-contract.md` | Interactive intake → full review + negotiation guidance |
| Contract Drafter | `.claude/agents/contract-drafter.md` | Drafts attorney-style contracts, with full reference boilerplate |
| Challenge Reviewer | `.claude/agents/challenge-reviewer.md` | Adversarial review: gaps, ambiguities, one-sided terms, exposure |
| Scenario Tester | `.claude/agents/scenario-tester.md` | Stress-tests against 60+ scenarios plus custom-generated ones |
| Risk scoring | `flows/risk-scoring.md` | Scoring methodology and report templates |
| Scenario library | `scenarios/scenario-library.md` | Universal + type-specific test cases |
| Business context | `my-business/` | Your profile, preferences, templates, past contracts (gitignored) |

## Usage

Open Claude Code in this directory. Then either:

**Use a slash command:**
```
/new-contract I'm hiring a marketing consultant for 6 months at $5k/month
/review-contract contract/vendor-agreement.md
```

**Or just ask** — `CLAUDE.md` routes plain requests to the right workflow:
```
"I need an NDA for sharing product designs with a manufacturer"
"Review this SaaS agreement — I'm worried about the liability section"
"Test contract/service-agreement.md against common dispute scenarios"
"What happens if the other party goes bankrupt under this contract?"
```

**Targeted single-agent tasks** work too — ask for a specific agent:
```
"Use the challenge-reviewer agent on this termination clause: ..."
"Use the scenario-tester agent on contract/nda.md"
```

### How a Generation Run Works

1. **Intake** — guided plain-English questions produce a confirmed CONTRACT INTAKE SUMMARY
2. **Draft** — the drafter subagent produces the contract in formal legal language
3. **Challenge** — the reviewer subagent (fresh context) finds gaps, ambiguities, one-sided terms; the drafter revises anything Medium risk or above
4. **Scenario test** — the tester subagent runs universal, type-specific, and custom scenarios
5. **Remediate** — failed scenarios get fixes, which are re-reviewed and re-tested
6. **Output** — final contract + risk-scored report in `output/`, with remaining limitations and attorney-review recommendations

### Common Use Cases

| I want to... | Do this |
|--------------|---------|
| Create a contract from scratch | `/new-contract [describe it]` |
| Review a contract I received | `/review-contract [path]` |
| Quick review of one clause | Ask for the challenge-reviewer on the pasted clause |
| Test if my contract handles X | Ask for the scenario-tester with your concern |
| Understand what questions to ask | Start `/new-contract` or `/review-contract` — the intake IS the question list |

### Tips for Best Results

1. **Be specific during intake** — "Marketing consultant for 6 months at $5k/month" beats "consultant"
2. **Don't skip the challenge phase** — every section gets reviewed, even boilerplate
3. **Take scenario failures seriously** — a failed scenario is a real gap in protection
4. **Set up `my-business/`** — a filled-in profile and preferences file makes every contract faster and more consistent (see `my-business/README.md`)
5. **Note state-specific issues** — employment, non-competes, and arbitration vary by state
6. **Always get attorney review** — AI-generated contracts need human legal review

## Customizing

| To change... | Edit |
|--------------|------|
| Intake questions | `.claude/commands/new-contract.md` / `review-contract.md` |
| Drafting style or reference boilerplate | `.claude/agents/contract-drafter.md` |
| Review rubric or issue categories | `.claude/agents/challenge-reviewer.md` |
| Test scenarios | `scenarios/scenario-library.md` and `.claude/agents/scenario-tester.md` |
| Risk thresholds | `flows/risk-scoring.md` |
| Workflow rules and quality gates | `CLAUDE.md` |

## Jurisdiction

Focused on US Federal/State law with state-specific callouts where relevant.

## Limitations

- This system generates templates, not legal advice
- Always have a licensed attorney review important contracts
- State-specific laws may require modifications
- Industry regulations may need additional provisions
- Complex transactions require human legal expertise

## Disclaimer

Contracts generated by this system are AI-created templates. They should be reviewed by a licensed attorney before use. This system does not provide legal advice and should not be relied upon as a substitute for professional legal counsel.
