---
description: Review a contract you received — interactive intake, then full challenge review and negotiation guidance
---

Run Workflow B (review a received contract) from CLAUDE.md. Start with the intake interview below, in the main conversation. The user has been handed a contract to sign and needs to understand what they're agreeing to, what risks they're taking, what to push back on, and what's standard vs. unusual. Plain English throughout; validate their gut feelings — concerns about clauses are often right.

If the user pointed at a contract file in `$ARGUMENTS`, read it after the intake so the review is informed by their situation. If they already explained their situation, confirm rather than re-asking.

## Business Context First

Check whether `my-business/profile/company.md` exists — if found, ask whether to use it. If `profile/preferences.md` has deal-breakers, use them as default walk-away points and confirm.

## Intake Interview

**1. The situation** — Did they receive this contract or is it someone's standard template? Relationship with the other party (new vs. existing, power dynamic, how important is the deal)? Is it negotiable or take-it-or-leave-it? Signing timeline? Signed similar contracts before — any problems?

**2. Their position** — What are they most worried about? Worst plausible outcome? Assets/IP/relationships needing protection? Walk-away points? What would make this deal a win?

**3. Their leverage** — Does the other party need them, or have alternatives? Do THEY have alternatives? What do they bring that the other side values? Any time pressure on the other party? Be realistic: if they have no leverage, help them understand their options rather than pretending they can negotiate everything.

**4. Concern areas** — walk through payment terms, performance obligations, termination rights, liability/indemnification, IP ownership, non-compete/exclusivity, and confidentiality, asking what confused or concerned them in each.

**5. Red flags** — ask specifically about: automatic renewal, unilateral term changes, prevailing-party/fee-shifting clauses, arbitration or jury-trial waivers, most-favored-nation pricing, and assignment clauses.

**6. Desired outcomes** — the three things they'd most want changed; what would make them feel safe signing; minimum needed to move forward; fallback positions and creative alternatives (shorter term, different payment structure).

If the timeline is tight, flag that negotiation room may be limited.

## Challenge Intake Summary

```markdown
## CONTRACT CHALLENGE INTAKE SUMMARY

### Contract Under Review
- **Type:** / **Other Party:** / **Value:** / **Term:** / **Signing Timeline:**
### Client's Position
- **Negotiating Power:** [High/Medium/Low/None]
- **Alternatives Available:** / **Importance of Deal:**
### Client's Top Concerns
### Walk-Away Points
### Must-Have Changes
### Nice-to-Have Changes
### Areas Flagged for Deep Review
### Notes for Challenge Review
```

Confirm with the user, then get the contract text (file path or pasted). Offer to save the summary to `my-business/history/`.

## Then Run the Review

Per CLAUDE.md Workflow B: `challenge-reviewer` subagent on the entire document with the intake summary as context → `scenario-tester` subagent prioritizing scenarios that match the user's concerns (see the priority matrix in `scenarios/scenario-library.md`) → produce negotiation guidance:

1. Issues prioritized by severity × the user's actual leverage
2. Specific redline language for each ask, in formal legal style matching the contract
3. Fallback positions for each must-have
4. Explicit "this is standard, don't spend capital fighting it" calls for acceptable terms

Output a risk report (per `flows/risk-scoring.md`), issue summary, and negotiation talking points to `output/`; a redlined version of the contract if requested.
