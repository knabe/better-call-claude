# Better Call Claude — Legal Contract System

Multi-agent contract generation and review for business owners who are not lawyers.

## The One Rule That Governs Everything

**Contract text = formal legal language. Everything said to the user = plain English.**

Generated contracts use proper legal terminology, recitals, defined terms, and formal structure — indistinguishable from attorney-drafted agreements. All questions, explanations, and guidance to the user are jargon-free plain English, with risks made concrete through real-world examples. Never assume legal knowledge.

## Components

| Component | Location | Kind |
|---|---|---|
| Contract Drafter | `.claude/agents/contract-drafter.md` | Subagent — drafts sections/contracts from an intake summary |
| Challenge Reviewer | `.claude/agents/challenge-reviewer.md` | Subagent — adversarial review with fresh context |
| Scenario Tester | `.claude/agents/scenario-tester.md` | Subagent — stress-tests contracts against scenario library |
| New-contract intake | `.claude/commands/new-contract.md` | Slash command — interactive questionnaire, then orchestrates |
| Contract-review intake | `.claude/commands/review-contract.md` | Slash command — interactive questionnaire, then orchestrates |
| Risk scoring methodology | `flows/risk-scoring.md` | Reference — read when scoring |
| Scenario library | `scenarios/scenario-library.md` | Reference — read when testing |

Intake is interactive and happens in the main conversation (subagents cannot ask the user questions). Drafting, challenging, and scenario testing are autonomous and run as subagents — the Challenge Reviewer and Scenario Tester deliberately get **fresh context** so they review the contract text on its merits, not the drafting conversation.

## Workflow A: Create a New Contract

Goal: an intake summary → a complete, challenge-tested, scenario-tested contract with a risk report.

1. **Intake** (main conversation, or `/new-contract`) — produce a CONTRACT INTAKE SUMMARY and get the user's confirmation before drafting.
2. **Draft** — Contract Drafter subagent produces the contract from the summary.
3. **Challenge** — Challenge Reviewer subagent reviews the draft. Independent sections can be reviewed by parallel subagents. Drafter revises anything at Medium risk or above; if an issue survives revision, surface it to the user as a decision rather than iterating indefinitely.
4. **Scenario test** — Scenario Tester subagent runs universal + type-specific + custom scenarios against the full draft.
5. **Remediate** — for each FAIL / NEEDS WORK: drafter proposes a fix, challenge reviewer checks the fix doesn't create new problems, scenario is re-run. Unresolvable gaps go to the user as decisions.
6. **Final output** — complete contract + risk report (per `flows/risk-scoring.md`) saved to `output/`, with remaining limitations and attorney-review recommendation.

**Quality gates** (verify before finishing, in any order the work happens):
- [ ] User confirmed the intake summary before drafting began
- [ ] Every section was challenge-reviewed — including boilerplate
- [ ] No CRITICAL issues unresolved; HIGH issues resolved or explicitly acknowledged by the user
- [ ] Scenario pass rate ≥ 80%, and every failure either fixed or surfaced to the user
- [ ] Final document includes the AI-generation disclaimer and attorney-review recommendation

## Workflow B: Review a Received Contract

Goal: the user's contract + their situation → a prioritized issue list with negotiation guidance.

1. **Intake** (main conversation, or `/review-contract`) — understand their position, leverage, deal-breakers, and top concerns; produce a CHALLENGE INTAKE SUMMARY.
2. **Full challenge review** — Challenge Reviewer subagent on the entire document, informed by the intake summary.
3. **Scenario test** — prioritize scenarios matching the user's stated concerns, then universal coverage.
4. **Negotiation guidance** — issues prioritized by severity × the user's leverage; specific redline language for each ask; fallback positions; explicit "this is standard, don't fight it" calls for acceptable terms.
5. **Output** — risk report + issue summary + negotiation talking points saved to `output/`; redlined contract if requested.

**Quality gates:**
- [ ] Every section analyzed, not just the flagged ones
- [ ] Recommendations account for the user's actual negotiating leverage
- [ ] Redline suggestions are in formal legal language matching the contract's style
- [ ] Risks communicated in plain English with real-world impact

## Business Context (`my-business/`)

Check the `my-business/` folder when the user references their business, standard terms, templates, or past deals — not upfront, only when relevant. Confirm before using ("I found your company profile — use this?"). Offer to save intake summaries to `my-business/history/` at the end of a session. See `my-business/README.md` for the folder layout. These folders are gitignored — they contain real business data.

## Hard Boundaries

- **Never give definitive legal advice.** This system produces templates and analysis, not counsel. Recommend attorney review for anything consequential, and always include the disclaimer on generated contracts.
- **Jurisdiction:** US Federal/State law. Flag state-specific issues (non-competes, arbitration, employment law) rather than guessing at one state's rules.
- Real client documents live in `contract/`, `output/`, and `my-business/` — all gitignored. Never commit them.
