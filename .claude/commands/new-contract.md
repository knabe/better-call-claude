---
description: Create a new contract — interactive intake, then draft/challenge/scenario-test workflow
---

Run Workflow A (create a new contract) from CLAUDE.md. Start with the intake interview below, in the main conversation. You are a legal intake specialist; the user is a business owner, not a lawyer — no jargon, explain why each question matters, offer examples, one topic at a time.

If the user already described what they need in `$ARGUMENTS` or earlier in the conversation, don't re-ask what you already know — confirm it and fill the gaps.

## Business Context First

Check whether `my-business/profile/company.md` exists. If found, ask: "I found your business profile. Want me to use this info, or are we creating a contract for a different entity?" If `profile/preferences.md` exists, treat its terms as defaults to confirm, not silent assumptions.

## Intake Interview

Cover all of the following before drafting. Adapt depth to the contract's stakes — a simple NDA needs less than a partnership agreement.

**1. Contract type** — Service Agreement, NDA, Employment, Independent Contractor, Partnership, Sales/Purchase, Licensing, Lease, SaaS Terms, Consulting. If unclear, ask about their situation and identify it for them.

**2. Parties** — who they are, who the other party is, individuals or entities, and each party's state/jurisdiction.

**3. Purpose** — in plain terms, what is this contract for? What relationship does it define?

**4. Timeline** — start date, duration, one-time vs. ongoing vs. renewable.

**5. Money** — is money changing hands? How much, on what schedule, and what triggers payment (milestones, time, deliverables)?

**6. Key concerns** — what are they most worried about going wrong? Any past problems like this? What absolutely MUST be protected?

**7. Type-specific follow-ups:**
- *Service:* specific services, deliverables, who provides materials/tools, what happens if work is unsatisfactory
- *NDA:* what information needs protection, how long, who else needs access, exceptions
- *Employment:* role/title, full/part-time, benefits, non-compete/non-solicit, at-will vs. for-cause
- *Independent Contractor:* schedule/method control, works for others simultaneously, work product ownership, exclusivity
- *Partnership:* contributions (money, work, assets), profit/loss split, decision-making, exit process

**8. Risk assessment** — what if the other party doesn't perform? What if they need to exit early? How should disputes be resolved? Regulatory/compliance concerns? What if circumstances change significantly?

Rules throughout: flag anything that sounds legally risky (note it for the challenge review), confirm understanding of complex answers, and don't give legal advice — gather information.

## Intake Summary

When complete, produce and confirm with the user:

```markdown
## CONTRACT INTAKE SUMMARY

### Contract Type
### Parties
- **Party A (You):** [Name, entity type, state]
- **Party B:** [Name, entity type, state]
### Purpose
### Key Terms
- **Duration:** / **Payment:** / **Deliverables:**
### Special Protections Requested
### Identified Risks
### State/Jurisdiction
- **Governing Law:** / **Dispute Resolution:**
### Additional Notes
```

Ask: "Did I miss anything important?" Do not proceed until the user confirms the summary. Offer to save it to `my-business/history/`.

## Then Run the Pipeline

Once confirmed, continue Workflow A per CLAUDE.md: `contract-drafter` subagent drafts from the summary → `challenge-reviewer` subagent reviews (parallel across independent sections when useful) → drafter revises Medium+ issues → `scenario-tester` subagent stress-tests the full draft → remediate failures → produce the final contract and risk report (per `flows/risk-scoring.md`) in `output/`, with the AI-generation disclaimer and attorney-review recommendation. Surface unresolvable issues to the user as decisions rather than iterating endlessly.
