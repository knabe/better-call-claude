# How to Use This System

## Quick Start

### Option 1: Full Orchestrator (Recommended)
Use `flows/orchestrator.md` as your system prompt. The orchestrator will guide you through the entire process and invoke the appropriate agents.

```
System: [Contents of flows/orchestrator.md]

User: I need to create a consulting agreement
```

### Option 2: Individual Agents
Use specific agents directly when you only need part of the workflow.

---

## Agent Reference

| Agent | File | Use When |
|-------|------|----------|
| Intake Questionnaire | `agents/01-intake-questionnaire.md` | Gathering requirements for a new contract |
| Contract Drafter | `agents/02-contract-drafter.md` | Writing contract sections |
| Challenge Agent | `agents/03-challenge-agent.md` | Reviewing contract for issues |
| Challenge Questionnaire | `agents/04-challenge-questionnaire.md` | Gathering info to review an existing contract |
| Scenario Tester | `agents/05-scenario-tester.md` | Stress-testing contracts |

---

## Workflow Examples

### Creating a New Contract

```
1. Load orchestrator.md as system prompt
2. Say: "I need to create a [contract type]"
3. Answer the intake questions
4. Review each section as it's drafted
5. Acknowledge any issues flagged
6. Review scenario test results
7. Receive final contract and risk report
```

### Reviewing an Existing Contract

```
1. Load orchestrator.md as system prompt
2. Say: "I received a contract I need to review"
3. Answer the challenge questionnaire
4. Paste/upload the contract text
5. Review issues identified
6. Get negotiation recommendations
```

### Just Challenging a Section

```
1. Load agents/03-challenge-agent.md as system prompt
2. Paste the contract section
3. Get detailed review with issues and recommendations
```

---

## Customizing for Your Needs

### Adding Contract Types
Edit `agents/01-intake-questionnaire.md` to add contract-type-specific questions.

### Adding Scenarios
Edit `scenarios/scenario-library.md` to add new test cases.

### Changing Risk Thresholds
Edit `flows/risk-scoring.md` to adjust what qualifies as Low/Medium/High/Critical.

---

## Tips

1. **Be specific in intake** - The more detail you provide, the better the contract
2. **Don't skip challenges** - Every section should be reviewed
3. **Take scenarios seriously** - Failed scenarios are real risks
4. **Keep disclaimers** - Always note AI generation and recommend attorney review
5. **Save outputs** - Keep risk reports for your records

---

## Limitations

- This system provides templates, not legal advice
- Always have a licensed attorney review important contracts
- State-specific laws may require modifications
- Industry-specific regulations may not be covered
- Complex transactions need human legal expertise
