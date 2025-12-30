# My Business Context

This folder stores your business information and contract history. The AI agents will reference these files when relevant to provide better, more personalized contracts.

**Note:** This folder is tracked in git. Add sensitive files (with real client names, financial details, etc.) to `.gitignore` or keep them in a separate untracked location.

---

## Folder Structure

```
my-business/
├── profile/        # Your business information
├── history/        # Q&A and session history
├── templates/      # Your custom contract templates
└── past-contracts/ # Previous contracts for reference
```

---

## What to Put in Each Folder

### `profile/` - Your Business Info

Add files describing your business. The agents will reference these when drafting contracts.

**Suggested files:**

| File | What to Include |
|------|-----------------|
| `company.md` | Business name, entity type (LLC, Corp), state, address, EIN |
| `services.md` | What services you offer, typical pricing, service areas |
| `team.md` | Key people, their roles, who can sign contracts |
| `insurance.md` | Your insurance coverage, policy numbers, limits |
| `preferences.md` | Default payment terms, preferred dispute resolution, deal-breakers |

**Example `company.md`:**
```markdown
# Company Profile

- **Name:** Jims Hair LLC
- **Entity Type:** Limited Liability Company
- **State of Formation:** New Jersey
- **Address:** 123 Test Street, Sheboygan, NJ 08005
- **EIN:** 12-3456789
- **Owner:** Jim Jones
- **Formed:** January 2020
```

**Example `preferences.md`:**
```markdown
# Contract Preferences

## Payment Terms
- Always require 50% deposit upfront
- Net 30 for balance unless otherwise specified
- Late fee: 1.5% per month

## Cancellation Policy
- 30 days notice required
- Deposit is always non-refundable

## Dispute Resolution
- Prefer mediation first, then arbitration
- Avoid litigation if possible
- Always New Jersey governing law

## Deal Breakers
- Never agree to unlimited liability
- Never waive right to collect attorney fees
- Always cap liability at contract value
```

---

### `history/` - Session History

The system can save Q&A sessions here for future reference.

**Auto-generated files:**
- `YYYY-MM-DD-contract-type.md` - Intake summaries
- `YYYY-MM-DD-session.md` - Full session transcripts

**Why this helps:** If you create similar contracts often, the agent can reference past sessions to speed up intake.

---

### `templates/` - Your Custom Templates

Drop your own contract templates here. The drafter agent can use these as starting points.

**Example files:**
- `my-standard-service-agreement.md`
- `my-nda-template.md`
- `wedding-services-v2.md`

**Format:** Plain text or markdown. Include placeholders like `[CLIENT_NAME]`, `[DATE]`, `[AMOUNT]`.

---

### `past-contracts/` - Previous Contracts

Store finalized contracts here for reference. Useful for:
- Maintaining consistency across similar deals
- Referencing terms you've agreed to before
- Building a clause library

**Suggested naming:** `YYYY-MM-DD-client-name-type.md`

---

## How Agents Use This Folder

| Agent | What It Checks |
|-------|----------------|
| **Intake Questionnaire** | `profile/` for default company info |
| **Contract Drafter** | `profile/preferences.md` for default terms, `templates/` for starting points |
| **Challenge Agent** | `past-contracts/` for consistency with previous deals |
| **Scenario Tester** | `profile/` for business-specific scenarios |

The agents check these folders **when relevant** - they don't read everything upfront. If you mention "use my standard terms" or "same as the Johnson contract," they'll look here.

---

## Privacy Note

This folder is tracked in git to provide example templates. If you add files containing sensitive information, either:
1. Add specific files to `.gitignore` (e.g., `my-business/past-contracts/`)
2. Keep sensitive data in a separate untracked folder

**Do not commit files containing:**
- Client names or contact info
- Financial details
- Signed contracts
- Any PII (personally identifiable information)
