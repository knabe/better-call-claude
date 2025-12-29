# Risk Scoring System

## Purpose
Provide clear, actionable risk assessment for each contract section and the overall document. Scores help users understand where to focus attention and what issues need addressing.

---

## Risk Levels

### Level 1: LOW (Score: 1)
**Color: Green**

Characteristics:
- Standard, balanced language
- Clear and unambiguous terms
- Well-established legal provisions
- Appropriate for the contract type
- No enforcement concerns

Action Required: None. Accept as-is.

### Level 2: MEDIUM (Score: 2)
**Color: Yellow**

Characteristics:
- Minor ambiguities present
- Slightly favors one party
- Missing nice-to-have provisions
- State-specific variations possible
- Small potential for dispute

Action Required: Consider addressing if time permits. Note for awareness.

### Level 3: HIGH (Score: 3)
**Color: Orange**

Characteristics:
- Significant gaps or ambiguities
- Clearly one-sided terms
- Missing important protections
- Potential enforcement issues
- Could lead to disputes

Action Required: Should address before signing/finalizing. Flag for client decision.

### Level 4: CRITICAL (Score: 4)
**Color: Red**

Characteristics:
- May be unenforceable
- Creates major liability exposure
- Missing essential terms
- Potential legal/regulatory issues
- Would recommend against signing as-is

Action Required: Must address. Do not proceed without resolution.

---

## Section Scoring

Each contract section receives a risk score based on:

### 1. Clarity Score (0-1 points)
- 1.0: Completely clear, no ambiguity
- 0.5: Minor ambiguities
- 0.0: Significant ambiguity

### 2. Balance Score (0-1 points)
- 1.0: Balanced/fair to both parties
- 0.5: Moderately one-sided
- 0.0: Heavily one-sided

### 3. Completeness Score (0-1 points)
- 1.0: All expected provisions present
- 0.5: Minor gaps
- 0.0: Major gaps

### 4. Enforceability Score (0-1 points)
- 1.0: Clearly enforceable
- 0.5: Some enforceability concerns
- 0.0: Likely unenforceable

### Section Risk Level Calculation
```
Raw Score = Clarity + Balance + Completeness + Enforceability
(Range: 0-4)

Risk Level:
- 3.5-4.0: LOW
- 2.5-3.4: MEDIUM
- 1.5-2.4: HIGH
- 0.0-1.4: CRITICAL
```

---

## Section Risk Scorecard Template

```markdown
## SECTION RISK SCORECARD: [Section Name]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Clarity | [0-1] | [Explanation] |
| Balance | [0-1] | [Explanation] |
| Completeness | [0-1] | [Explanation] |
| Enforceability | [0-1] | [Explanation] |
| **Total** | **[0-4]** | |

### Risk Level: [LOW/MEDIUM/HIGH/CRITICAL]

### Issues Found
| Issue | Type | Severity | Recommendation |
|-------|------|----------|----------------|
| [Issue 1] | [AMBIGUITY/GAP/ONE-SIDED/etc] | [H/M/L] | [Fix] |

### Client Action Required
- [ ] [Action item if any]
```

---

## Overall Contract Score

### Weighted Section Importance
Different sections have different weights based on importance:

| Section | Weight | Rationale |
|---------|--------|-----------|
| Parties/Recitals | 1.0 | Essential for validity |
| Scope | 1.5 | Core obligations |
| Term/Termination | 1.5 | Exit rights critical |
| Payment | 1.5 | Usually primary concern |
| Deliverables | 1.5 | Performance clarity |
| IP | 1.0 | Important if applicable |
| Confidentiality | 1.0 | Standard importance |
| Warranties | 1.0 | Moderate exposure |
| Liability Limits | 2.0 | Major exposure area |
| Indemnification | 2.0 | Major exposure area |
| Dispute Resolution | 1.0 | Process matters |
| General Provisions | 0.5 | Standard boilerplate |

### Overall Score Calculation
```
Overall Score = Σ(Section Score × Weight) / Σ(Weights)
```

### Overall Risk Rating

```
Overall Score Range → Rating:
- 3.5-4.0: LOW RISK CONTRACT
- 2.5-3.4: MODERATE RISK CONTRACT
- 1.5-2.4: HIGH RISK CONTRACT
- 0.0-1.4: CRITICAL RISK CONTRACT
```

---

## Scenario Testing Impact

Scenario test results affect overall score:

### Scenario Pass Rate Modifier
```
Pass Rate 90-100%: No modifier
Pass Rate 75-89%:  -0.2 to overall score
Pass Rate 50-74%:  -0.5 to overall score
Pass Rate < 50%:   -1.0 to overall score
```

### Critical Scenario Failures
If any scenario marked CRITICAL fails:
- Overall score capped at 2.5 (HIGH RISK) until resolved
- Regardless of section scores

---

## Risk Report Template

```markdown
# CONTRACT RISK ASSESSMENT REPORT

## Summary

| Metric | Value |
|--------|-------|
| Contract Type | [Type] |
| Overall Risk Level | [LOW/MEDIUM/HIGH/CRITICAL] |
| Overall Score | [X.X / 4.0] |
| Scenarios Tested | [X] |
| Scenario Pass Rate | [X%] |

## Section Scores

| Section | Score | Risk Level | Issues |
|---------|-------|------------|--------|
| Parties | [X.X] | [Level] | [Count] |
| Scope | [X.X] | [Level] | [Count] |
| Term/Termination | [X.X] | [Level] | [Count] |
| ... | ... | ... | ... |

## Critical Issues (Must Address)

| # | Section | Issue | Impact | Recommendation |
|---|---------|-------|--------|----------------|
| 1 | [Section] | [Issue] | [What could go wrong] | [How to fix] |

## High Priority Issues (Should Address)

| # | Section | Issue | Impact | Recommendation |
|---|---------|-------|--------|----------------|
| 1 | [Section] | [Issue] | [What could go wrong] | [How to fix] |

## Medium Priority Issues (Consider Addressing)

| # | Section | Issue | Impact | Recommendation |
|---|---------|-------|--------|----------------|
| 1 | [Section] | [Issue] | [What could go wrong] | [How to fix] |

## Scenario Test Results

### Failed Scenarios
| Scenario | Gap | Recommendation |
|----------|-----|----------------|
| [ID: Name] | [What's missing] | [Add to contract] |

### Scenarios Needing Work
| Scenario | Issue | Recommendation |
|----------|-------|----------------|
| [ID: Name] | [Partial coverage] | [Strengthen language] |

## Recommendations

### Before Signing
1. [Action item]
2. [Action item]
3. [Action item]

### Additional Protections to Consider
1. [Optional protection]
2. [Optional protection]

### Monitoring After Signing
1. [What to watch for]
2. [When to revisit terms]

## Limitations

This assessment:
- Was generated by AI and should be reviewed by a licensed attorney
- Is based on general principles and may not address jurisdiction-specific issues
- Does not constitute legal advice
- May not cover all possible scenarios or risks

---
Generated: [Date]
Assessment ID: [ID]
```

---

## Visual Risk Indicators

### For UI/Display
Use these indicators when displaying risk levels:

```
LOW:      🟢 ✓ (green circle/check)
MEDIUM:   🟡 ⚠ (yellow circle/warning)
HIGH:     🟠 ⚠ (orange circle/warning)
CRITICAL: 🔴 ✗ (red circle/x)
```

### Progress Bar (Optional)
```
Score 4.0: ████████████████████ 100%
Score 3.0: ███████████████░░░░░  75%
Score 2.0: ██████████░░░░░░░░░░  50%
Score 1.0: █████░░░░░░░░░░░░░░░  25%
```

---

## Quick Reference: Risk Response

| Risk Level | Client Action | Agent Action |
|------------|---------------|--------------|
| LOW | May proceed | Document and move on |
| MEDIUM | Note and consider | Flag for awareness |
| HIGH | Address before proceeding | Require revision or acknowledgment |
| CRITICAL | Must resolve | Block progress until resolved |
