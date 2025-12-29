# Better Call Claude

*Multi-agent contract generation with built-in challenge testing*

A Claude-powered system for generating, challenging, and stress-testing legal contracts for business owners.

## Language Philosophy

| What | Language Style |
|------|----------------|
| **Generated Contracts** | Professional legal language (formal, attorney-style drafting) |
| **Explanations to Users** | Plain English (accessible, jargon-free) |

Contracts are drafted with proper legal terminology, recitals, whereas clauses, and formal structure - indistinguishable from attorney-drafted agreements. All explanations, questions, and guidance are in plain English so non-lawyers understand what they're signing.

## Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                         ORCHESTRATOR                                 │
│                    (flows/orchestrator.md)                          │
└─────────────────────────────────────────────────────────────────────┘
                                │
        ┌───────────────────────┼───────────────────────┐
        ▼                       ▼                       ▼
┌───────────────┐      ┌───────────────┐      ┌───────────────┐
│    INTAKE     │      │   CHALLENGE   │      │   SCENARIO    │
│ QUESTIONNAIRE │      │ QUESTIONNAIRE │      │    TESTER     │
│    AGENT      │      │    AGENT      │      │    AGENT      │
└───────┬───────┘      └───────┬───────┘      └───────┬───────┘
        │                      │                      │
        ▼                      ▼                      │
┌───────────────┐      ┌───────────────┐              │
│   CONTRACT    │◄────►│   CHALLENGE   │◄─────────────┘
│    DRAFTER    │      │    AGENT      │
│    AGENT      │      │               │
└───────────────┘      └───────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────────────────────┐
│                      RISK SCORING & OUTPUT                            │
└───────────────────────────────────────────────────────────────────────┘
```

## Agents

| Agent | Purpose |
|-------|---------|
| **Intake Questionnaire** | Gathers requirements through guided questions for non-lawyers |
| **Contract Drafter** | Generates professional legal language contracts (attorney-style) |
| **Challenge Agent** | Reviews for weaknesses, gaps, one-sided terms; explains issues in plain English |
| **Challenge Questionnaire** | Gathers info for reviewing/challenging existing contracts |
| **Scenario Tester** | Runs edge cases against contract to find gaps |

## Flow

1. **Intake Phase** - Questionnaire agent gathers all requirements
2. **Draft Phase** - Drafter creates sections iteratively
3. **Challenge Phase** - Each section is challenged and revised
4. **Scenario Phase** - Full document tested against scenarios
5. **Final Output** - Risk-scored markdown document

## Usage

### Quick Start

There are three ways to use this system:

1. **Full Orchestrator** - Use for complete contract generation or review workflows
2. **Individual Agents** - Use specific agents for targeted tasks
3. **Claude Code Integration** - Define agents in your Claude Code configuration

---

### Method 1: Full Orchestrator (Recommended)

Load `flows/orchestrator.md` as your system prompt for the complete workflow.

**Example: Creating a New Contract**

```
SYSTEM PROMPT: [paste contents of flows/orchestrator.md]

USER: I need to create a consulting agreement for a marketing consultant

ASSISTANT: Welcome to the Legal Document Assistant.

I'll help you create a consulting agreement. Let me gather some information.

First, tell me about yourself - the company or person hiring the consultant.
- What is your name/company name?
- Are you a business entity (LLC, Corp) or individual?
- What state are you in?

USER: We're TechStart Inc, a Delaware C-Corp based in California.

ASSISTANT: Great. Now about the consultant...
[continues through intake questions]
```

**Example: Reviewing an Existing Contract**

```
SYSTEM PROMPT: [paste contents of flows/orchestrator.md]

USER: I received a contract from a vendor that I need to review before signing

ASSISTANT: I'll help you review this contract. First, let me understand your situation.

Did you receive this contract, or are you being asked to sign someone else's template?

USER: They sent me their standard vendor agreement

ASSISTANT: What is your relationship with this vendor?
- Is this a new relationship or existing?
- Are they a larger company than you?
- How important is this deal?

USER: New vendor, they're much bigger than us, but we have other options

ASSISTANT: Good - having alternatives gives you negotiating power...
[continues through challenge questionnaire]
```

---

### Method 2: Individual Agents

Use specific agents directly when you only need part of the workflow.

**Example: Just Challenge a Contract Section**

```
SYSTEM PROMPT: [paste contents of agents/03-challenge-agent.md]

USER: Review this termination clause:

"Either party may terminate this Agreement at any time for any reason.
Upon termination, all obligations cease immediately."

ASSISTANT:
---
## CHALLENGE REVIEW: Termination Clause
### Overall Section Risk: High
---

### Issues Found: 3

#### Issue 1
- **Type:** GAP
- **Text:** "at any time for any reason"
- **Problem:** No notice period required. Either party can terminate instantly.
- **Real-World Impact:** You could lose a critical vendor overnight with no transition time,
  or they could cut off your income with no warning.
- **Recommendation:** Add "with 30 days prior written notice"
- **Risk Level:** High

#### Issue 2
- **Type:** GAP
- **Text:** "all obligations cease immediately"
- **Problem:** Confidentiality, IP ownership, and payment obligations should survive termination.
- **Real-World Impact:** They could claim confidentiality ends when contract ends.
  Unpaid invoices could be disputed.
- **Recommendation:** Add survival clause for Sections X, Y, Z
- **Risk Level:** High

#### Issue 3
- **Type:** AMBIGUITY
- **Text:** No mention of cause vs. convenience
- **Problem:** No distinction between terminating because someone breached vs. just wanting out.
- **Real-World Impact:** No cure period if you make a minor mistake - they could terminate immediately.
- **Recommendation:** Add separate "termination for cause" with notice and cure period.
- **Risk Level:** Medium
```

**Example: Run Scenarios Against a Contract**

```
SYSTEM PROMPT: [paste contents of agents/05-scenario-tester.md]

USER: Test this NDA against common scenarios:

[paste NDA text]

ASSISTANT:
## SCENARIO TEST: NDA-1 (Accidental Disclosure)

### Scenario Description
An employee accidentally emails confidential information to an external party.

### Contract Coverage
- **Addressed:** Partially
- **Relevant Sections:** Section 3 (Confidentiality Obligations)

### Analysis
Contract requires "reasonable measures" to protect information but doesn't define what
happens if a breach occurs despite reasonable measures.

Gap: No notification requirement. No process for containing breach. No limitation on
liability for accidental vs. intentional disclosure.

### Verdict
- **Status:** NEEDS WORK
- **Risk Level:** Medium
- **Recommendation:** Add breach notification requirements (within 48 hours) and
  distinguish between negligent and willful disclosure for remedies.

---

## SCENARIO TEST: NDA-4 (Compelled Disclosure)
[continues through scenarios...]
```

---

### Method 3: Claude Code Integration

Define agents in your Claude Code setup for easy invocation.

**In your Claude Code configuration, add custom agents:**

```json
{
  "agents": {
    "legal-intake": {
      "description": "Gather requirements for a new contract",
      "prompt_file": "agents/01-intake-questionnaire.md"
    },
    "legal-drafter": {
      "description": "Draft contract sections",
      "prompt_file": "agents/02-contract-drafter.md"
    },
    "legal-challenge": {
      "description": "Review contract for weaknesses",
      "prompt_file": "agents/03-challenge-agent.md"
    },
    "legal-scenarios": {
      "description": "Stress-test contract with scenarios",
      "prompt_file": "agents/05-scenario-tester.md"
    }
  }
}
```

**Then invoke via Claude Code:**

```bash
# Start full contract generation
claude "Use the legal-intake agent to help me create an NDA"

# Challenge a specific file
claude "Use the legal-challenge agent to review contracts/vendor-agreement.md"

# Run scenario tests
claude "Use the legal-scenarios agent to test contracts/service-agreement.md"
```

---

### Multi-Agent Workflow Example

Here's how the agents work together in practice:

```
Step 1: INTAKE AGENT
────────────────────
User: "I need an independent contractor agreement"

Agent asks:
→ Who are the parties?
→ What work will be performed?
→ Payment terms?
→ Duration?
→ Concerns?

Output: CONTRACT INTAKE SUMMARY


Step 2: DRAFTER AGENT (Section by Section)
──────────────────────────────────────────
Input: CONTRACT INTAKE SUMMARY

Drafts Section 1: Parties and Recitals
  ↓
CHALLENGE AGENT reviews → finds 1 minor issue → Low Risk → PASS
  ↓
Drafts Section 2: Definitions
  ↓
CHALLENGE AGENT reviews → no issues → Low Risk → PASS
  ↓
Drafts Section 3: Scope of Services
  ↓
CHALLENGE AGENT reviews → finds 2 issues → High Risk → REVISE
  ↓
Drafter revises Section 3 v2
  ↓
CHALLENGE AGENT reviews → issues resolved → Low Risk → PASS
  ↓
[continues through all sections]


Step 3: SCENARIO TESTER AGENT
─────────────────────────────
Input: Complete draft contract

Runs:
→ Universal scenarios (U-1 through U-10)
→ Independent Contractor scenarios (IC-1 through IC-10)
→ Custom scenarios based on this specific contract

Output:
- 18 scenarios tested
- 15 PASS
- 2 NEEDS WORK
- 1 FAIL

Step 4: GAP REMEDIATION
───────────────────────
For each FAIL/NEEDS WORK:

DRAFTER proposes fix → CHALLENGE reviews → Re-run scenario

Output: All scenarios now PASS


Step 5: FINAL OUTPUT
────────────────────
- Complete contract (Markdown)
- Risk score report
- Remaining limitations
- Attorney review recommendations
```

---

### Common Use Cases

| I want to... | Use this approach |
|--------------|-------------------|
| Create a contract from scratch | Full Orchestrator → "I need to create a [type]" |
| Review a contract I received | Full Orchestrator → "I received a contract to review" |
| Quick review of one clause | Challenge Agent only |
| Test if my contract handles X | Scenario Tester only |
| Improve a section I already wrote | Drafter + Challenge Agent |
| Understand what questions to ask | Intake or Challenge Questionnaire |

---

### Tips for Best Results

1. **Be specific during intake** - "Marketing consultant for 6 months at $5k/month" beats "consultant"
2. **Don't skip the challenge phase** - Every section should be reviewed, even boilerplate
3. **Take scenario failures seriously** - A failed scenario is a real gap in protection
4. **Iterate when needed** - It's fine to revise sections 2-3 times
5. **Note state-specific issues** - Employment, non-competes, and arbitration vary by state
6. **Always get attorney review** - AI-generated contracts need human legal review

---

### Sample Prompts to Try

**Creating contracts:**
```
"I need an NDA for sharing product designs with a manufacturer"
"Create a service agreement for my web development agency"
"I'm hiring a fractional CFO - I need a consulting agreement"
"Draft a partnership agreement for my 50/50 business partner"
```

**Reviewing contracts:**
```
"Review this SaaS agreement - I'm worried about the liability section"
"Is this non-compete enforceable in California?"
"What are the problems with this vendor contract?"
"Help me negotiate better terms for this lease"
```

**Testing contracts:**
```
"What happens if the other party goes bankrupt under this contract?"
"Test this agreement against common dispute scenarios"
"Would this contract protect me if they deliver late?"
```

---

## File Reference

| File | Purpose | When to Use |
|------|---------|-------------|
| `flows/orchestrator.md` | Main coordinator | Full workflows |
| `flows/risk-scoring.md` | Scoring methodology | Understanding risk levels |
| `agents/01-intake-questionnaire.md` | Requirements gathering | Starting new contracts |
| `agents/02-contract-drafter.md` | Section drafting | Writing contract text |
| `agents/03-challenge-agent.md` | Issue identification | Reviewing any contract |
| `agents/04-challenge-questionnaire.md` | Review intake | Reviewing received contracts |
| `agents/05-scenario-tester.md` | Stress testing | Finding gaps |
| `scenarios/scenario-library.md` | Test case library | Reference for testing |
| `examples/example-workflow.md` | Full walkthrough | Learning the system |

---

## Jurisdiction

Focused on US Federal/State law with state-specific callouts where relevant.

---

## Limitations

- This system generates templates, not legal advice
- Always have a licensed attorney review important contracts
- State-specific laws may require modifications
- Industry regulations may need additional provisions
- Complex transactions require human legal expertise

---

## Disclaimer

Contracts generated by this system are AI-created templates. They should be reviewed by a licensed attorney before use. This system does not provide legal advice and should not be relied upon as a substitute for professional legal counsel.
