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

### How These Files Work

Each `.md` file in this repo is a **prompt** - instructions that tell Claude how to behave. You give Claude the prompt, then have a conversation with it.

**Three ways to use them:**

| Method | Best For | Setup |
|--------|----------|-------|
| Claude.ai Projects | Easiest, persistent | Add files to a Project |
| Claude API | Developers, automation | Pass as `system` parameter |
| Claude Code | CLI users | Reference in conversation |

---

### Method 1: Claude.ai Projects (Recommended)

1. Go to [claude.ai](https://claude.ai) and create a new **Project**
2. In Project Settings, add the files you want to use:
   - For full workflow: upload `flows/orchestrator.md`
   - For specific tasks: upload individual agent files from `agents/`
3. Start a conversation in that Project
4. Claude will automatically follow the instructions in the uploaded files

**Example conversation after setup:**

```
YOU: I need to create a consulting agreement for a marketing consultant

CLAUDE: Welcome to the Legal Document Assistant.

I'll help you create a consulting agreement. Let me gather some information.

First, tell me about yourself - the company or person hiring the consultant.
- What is your name/company name?
- Are you a business entity (LLC, Corp) or individual?
- What state are you in?

YOU: We're TechStart Inc, a Delaware C-Corp based in California.

CLAUDE: Great. Now about the consultant...
```

---

### Method 2: Claude API

Pass the file contents as the `system` parameter:

```python
import anthropic

# Read the orchestrator prompt
with open("flows/orchestrator.md", "r") as f:
    system_prompt = f.read()

client = anthropic.Anthropic()
message = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=4096,
    system=system_prompt,
    messages=[
        {"role": "user", "content": "I need to create a consulting agreement"}
    ]
)
```

---

### Method 3: Claude Code CLI

Reference the files directly in your conversation:

```bash
# Start Claude Code in this directory
claude

# Then in the conversation:
> Read flows/orchestrator.md and use it as your instructions.
> I need to create a consulting agreement.
```

Or copy the file contents into your first message.

---

### Using Individual Agents

You don't have to use the full orchestrator. Pick the agent you need:

| I want to... | Use this file |
|--------------|---------------|
| Create a new contract | `flows/orchestrator.md` (full flow) |
| Just gather requirements | `agents/01-intake-questionnaire.md` |
| Just draft contract language | `agents/02-contract-drafter.md` |
| Review a contract for problems | `agents/03-challenge-agent.md` |
| Prepare to negotiate a contract I received | `agents/04-challenge-questionnaire.md` |
| Stress-test a contract with scenarios | `agents/05-scenario-tester.md` |

---

### Example: Challenging a Contract Section

Using `agents/03-challenge-agent.md`:

```
YOU: Review this termination clause:

"Either party may terminate this Agreement at any time for any reason.
Upon termination, all obligations cease immediately."

CLAUDE:
---
## CHALLENGE REVIEW: Termination Clause
### Overall Section Risk: High
---

### Issues Found: 3

#### Issue 1
- **Type:** GAP
- **Text:** "at any time for any reason"
- **Problem:** No notice period required...
[Claude provides detailed analysis]
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
