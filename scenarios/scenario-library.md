# Scenario Library

Pre-built test scenarios organized by contract type. Use these as a baseline and supplement with custom scenarios for each specific contract.

---

## Universal Scenarios (All Contract Types)

These scenarios should be tested against EVERY contract regardless of type:

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| U-1 | Party Goes Bankrupt | Other party files for bankruptcy mid-contract | Termination rights? Priority of claims? |
| U-2 | Assignment Without Consent | Party tries to assign contract to unknown third party | Assignment restrictions in place? |
| U-3 | Catastrophic Event | Pandemic/disaster prevents performance | Force majeure provisions? |
| U-4 | Material Breach Dispute | Parties disagree whether breach occurred | "Material breach" defined? Cure period? |
| U-5 | Communication Breakdown | Party becomes unresponsive | Notice provisions clear? Default remedies? |
| U-6 | Regulatory Change | New law affects contract viability | Renegotiation provisions? |
| U-7 | Confidential Leak | Protected info is disclosed | Remedies defined? Damages calculable? |
| U-8 | Merger/Acquisition | One party is acquired by competitor | Change of control clause? |
| U-9 | Key Person Departure | Essential contact/performer leaves | Substitution rights? Obligations survive? |
| U-10 | Interpretation Dispute | Parties read same clause differently | Dispute resolution clear? |

---

## Service Agreement Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| SA-1 | Deliverable Rejected | Client says work doesn't meet specifications | Acceptance criteria defined? Revision process? |
| SA-2 | Scope Creep | Client requests additions not in SOW | Change order process? Additional fees? |
| SA-3 | Vendor Substitution | Provider wants to swap subcontractor | Approval required? Client rights? |
| SA-4 | Deadline Missed | Provider delivers 30 days late | Damages defined? Termination trigger? |
| SA-5 | Quality Decline | Work quality drops after first deliverable | Quality standards? Cure process? |
| SA-6 | Over-Budget | Estimated expenses exceeded by 200% | Caps in place? Approval for overages? |
| SA-7 | Client Non-Cooperation | Client doesn't provide required inputs | Timeline extension? Cost allocation? |
| SA-8 | Incomplete Documentation | Provider delivers work but no docs/training | Deliverables list complete? |
| SA-9 | Warranty Claim | Bug found 6 months after completion | Warranty period? Scope of fixes? |
| SA-10 | Exit Transition | Contract ends, new vendor needs handoff | Transition assistance? Data transfer? |

---

## NDA Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| NDA-1 | Accidental Disclosure | Employee emails confidential info externally | Breach clear? Remedies proportionate? |
| NDA-2 | Public Knowledge Defense | Discloser claims info became public | Public info exception clear? |
| NDA-3 | Prior Knowledge Defense | Receiver claims they already knew info | Prior possession exception defined? |
| NDA-4 | Compelled Disclosure | Receiver subpoenaed for protected info | Legal exception? Notice required? |
| NDA-5 | Residual Knowledge | Receiver uses insights (not specifics) | Residuals clause present? Clear? |
| NDA-6 | Infinite Duration | 99-year confidentiality obligation | Duration reasonable? Enforceable? |
| NDA-7 | Overbroad Definition | "Everything discussed" is confidential | Confidential info clearly defined? |
| NDA-8 | Return of Materials | Relationship ends, materials not returned | Return/destruction requirements? |
| NDA-9 | Third Party Request | Third party asks for protected info | Obligations to resist? Notification? |
| NDA-10 | Derivative Works | Receiver creates analysis from confidential data | Derivatives addressed? |

---

## Employment Contract Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| EMP-1 | Termination Dispute | Employee fired, claims it wasn't for cause | "Cause" clearly defined? |
| EMP-2 | Non-Compete Challenge | Employee takes competing job | Scope/duration enforceable in state? |
| EMP-3 | Bonus Dispute | Employee claims promised bonus not paid | Bonus terms clear? Discretionary? |
| EMP-4 | IP Ownership Fight | Employee claims they own work created | Work-for-hire valid? Scope clear? |
| EMP-5 | Garden Leave Issues | Employee on garden leave works for competitor | Garden leave terms enforceable? |
| EMP-6 | Handbook Conflict | Contract says one thing, handbook another | Which controls? Integration clause? |
| EMP-7 | Reasonable Accommodation | Employee needs accommodation not addressed | Flexibility in duties? Process? |
| EMP-8 | Remote Work Dispute | Employee wants to work remotely indefinitely | Work location terms? |
| EMP-9 | Performance Improvement | Employee on PIP claims it's pretextual | PIP process defined? Objectivity? |
| EMP-10 | Resignation Notice | Employee resigns with less notice than required | Consequences of short notice? |

---

## Independent Contractor Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| IC-1 | Misclassification Claim | Contractor claims they're really employee | Control factors addressed? |
| IC-2 | Exclusivity Violation | Contractor works for competitor | Exclusivity terms? Reasonable? |
| IC-3 | Equipment Dispute | Who provides/owns equipment? | Terms clear? |
| IC-4 | Hours Creep | "Part-time" work becomes full-time expectation | Hours terms? Scope control? |
| IC-5 | Benefits Request | Contractor asks for benefits | Independent status clear? |
| IC-6 | Work Product Ownership | Contractor claims IP rights in deliverables | Assignment clear? Consideration? |
| IC-7 | Tax Withholding Issue | IRS claims withholding required | Indemnification for reclassification? |
| IC-8 | Insurance Gap | Contractor's insurance lapsed | Insurance requirements? Verification? |
| IC-9 | Substitution Attempt | Contractor sends substitute to do work | Substitution rights? Approval? |
| IC-10 | Multi-Year Engagement | "Short project" becomes 3-year relationship | Term limits? Re-evaluation? |

---

## Partnership Agreement Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| PA-1 | Unequal Contributions | One partner stops contributing | Contribution requirements? Remedies? |
| PA-2 | Decision Deadlock | Partners 50/50 split can't agree | Deadlock resolution? |
| PA-3 | Exit Request | Partner wants to leave | Buyout process? Valuation method? |
| PA-4 | Profit Dispute | Disagreement on profit calculation | Accounting method defined? |
| PA-5 | Personal Guarantee | Partner asked to personally guarantee | Scope of guarantees? |
| PA-6 | Competing Venture | Partner starts similar business | Competition restrictions? |
| PA-7 | Death of Partner | Partner dies unexpectedly | Succession? Buy-sell? Insurance? |
| PA-8 | Capital Call | Partnership needs cash infusion | Capital call process? |
| PA-9 | Partner Bankruptcy | Partner has personal financial crisis | Effects on partnership? Buyout? |
| PA-10 | Reputation Damage | Partner actions harm business reputation | Removal process? Standards? |

---

## SaaS/Software Agreement Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| SW-1 | Outage Incident | Service down for 48 hours | SLA defined? Credits? |
| SW-2 | Data Loss | Customer data accidentally deleted | Backup obligations? Liability? |
| SW-3 | Feature Removal | Vendor removes feature customer relies on | Feature guarantees? |
| SW-4 | Price Increase | Vendor raises prices 50% at renewal | Price protection? Caps? |
| SW-5 | Security Breach | Customer data exposed in breach | Notification? Indemnity? |
| SW-6 | Integration Break | Vendor update breaks customer's integration | Compatibility obligations? |
| SW-7 | Export Request | Customer wants to leave, needs data | Data portability? Format? |
| SW-8 | Usage Spike | Customer exceeds usage limits | Overage pricing? Warning? |
| SW-9 | Third Party Access | Vendor uses customer data for AI training | Data use rights clear? |
| SW-10 | Service Sunset | Vendor discontinues product | Notice period? Migration help? |

---

## Lease/Rental Agreement Scenarios

| ID | Name | Description | Key Questions |
|----|------|-------------|---------------|
| LS-1 | Maintenance Emergency | Major repair needed immediately | Response times? Cost allocation? |
| LS-2 | Early Termination | Tenant needs to break lease early | Penalty? Mitigation requirements? |
| LS-3 | Subletting Request | Tenant wants to sublet | Approval process? Conditions? |
| LS-4 | Property Damage | Major damage beyond normal wear | Damage definition? Insurance? |
| LS-5 | Noise/Nuisance | Complaints about tenant's activities | Use restrictions clear? |
| LS-6 | Renewal Terms | Parties disagree on renewal terms | Auto-renewal? Rate escalation? |
| LS-7 | Utility Dispute | Unexpected utility costs | Responsibility clear? |
| LS-8 | Security Deposit | Dispute over deposit return | Deduction criteria clear? |
| LS-9 | Access Rights | Landlord enters without proper notice | Access terms defined? |
| LS-10 | Assignment on Sale | Property sold to new landlord | Lease survives? Terms? |

---

## How to Use This Library

### For New Contracts (Generation Flow)
1. Identify contract type
2. Run ALL Universal Scenarios
3. Run ALL type-specific scenarios
4. Generate 3-5 custom scenarios based on specific terms
5. Document gaps and recommendations

### For Existing Contracts (Review Flow)
1. Identify contract type
2. Prioritize scenarios based on client concerns
3. Run high-priority scenarios first
4. Use failures to guide negotiation points
5. Run remaining scenarios for completeness

### Scenario Selection Matrix

| If client is concerned about... | Prioritize these scenarios... |
|--------------------------------|------------------------------|
| Getting paid | $-1 through $-5 |
| Protecting IP | IP-1 through IP-5 |
| Being able to exit | T-1 through T-5 |
| Limiting liability | D-1 through D-5 |
| Other party's performance | P-1 through P-5 |
| Confidentiality | NDA-1 through NDA-10 |
