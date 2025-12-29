# Example Workflow: Consulting Agreement

This example demonstrates the full contract generation flow for a consulting agreement.

**Key Concept:** The contract text uses formal legal language (attorney-style), while all explanations to the user are in plain English.

---

## Phase 1: Intake

### User Initiates
```
User: I need a contract for a consultant I'm hiring
```

### Intake Questionnaire Agent Conversation

**Agent:** I'll help you create a consulting agreement. Let me gather some information.

First, tell me about yourself - the company or person hiring the consultant.
- What is your name/company name?
- Are you a business entity (LLC, Corp) or individual?
- What state are you in?

**User:** We're TechStart Inc, a Delaware C-Corp, based in California.

**Agent:** Great. Now about the consultant:
- What is their name?
- Are they an individual or do they have their own company?
- What state are they in?

**User:** John Smith, he's an individual in Texas.

**Agent:** What will John be doing for you? Describe the work in plain terms.

**User:** He's going to help us build our marketing strategy. Create a go-to-market plan, help with positioning, maybe review some of our materials.

**Agent:** How long do you want this engagement to last?
- Fixed term (e.g., 3 months)?
- Ongoing until either party ends it?
- Project-based (ends when work is done)?

**User:** Let's do 6 months, with option to extend.

**Agent:** How will payment work?
- Hourly rate?
- Monthly retainer?
- Project-based fee?
- Something else?

**User:** Monthly retainer of $5,000, paid at the beginning of each month.

**Agent:** What are you most concerned about with this arrangement? Common concerns include:
- Protecting your company's confidential information
- Making sure you own the work product
- Being able to end the relationship if it's not working
- Making sure he doesn't work for competitors

**User:** All of those, especially the confidential info and owning the work. We're a startup with proprietary tech.

**Agent:** Good to know. A few more questions:
- Will John be working with any of your proprietary technology or source code?
- Will he have access to customer data?
- Are there specific competitors you're worried about?

**User:** Yes to tech access, no to customer data. Our main competitors are MarketCo and StrategyPlus.

**Agent:** How should disputes be handled if something goes wrong?

**User:** I don't know, what's typical?

**Agent:** Common options are:
- Go to court (litigation) - traditional but expensive
- Arbitration - faster, private, but less appeal rights
- Mediation first, then one of the above

For consulting agreements, many companies prefer arbitration because it's quicker and private.

**User:** Let's do mediation first, then arbitration if that doesn't work.

### Intake Summary Output

```markdown
## CONTRACT INTAKE SUMMARY

### Contract Type
Consulting/Independent Contractor Agreement

### Parties
- **Party A (Client):** TechStart Inc, Delaware C-Corp, California
- **Party B (Consultant):** John Smith, Individual, Texas

### Purpose
Marketing strategy development including:
- Go-to-market plan creation
- Positioning strategy
- Marketing materials review

### Key Terms
- **Duration:** 6 months with renewal option
- **Payment:** $5,000/month retainer, paid monthly in advance
- **Deliverables:** Marketing strategy documents, GTM plan

### Special Protections Requested
- Strong confidentiality (consultant will access proprietary tech)
- Clear IP ownership (all work product to Client)
- Non-compete covering MarketCo and StrategyPlus
- Termination flexibility

### Identified Risks
- Consultant in different state (Texas) - employment law considerations
- Access to proprietary technology - heightened confidentiality needs
- Startup context - need clear IP assignment

### State/Jurisdiction
- **Governing Law:** California (Client's state)
- **Dispute Resolution:** Mediation, then binding arbitration

### Additional Notes
- No access to customer data
- Consultant is individual, not entity (ensure proper contractor classification)
```

---

## Phase 2: Iterative Drafting

### Section 1: Preamble and Recitals

**Contract Drafter Output:**

```markdown
---
## SECTION: Preamble and Recitals
### Draft Version: 1
### Risk Level: Low
---

                         CONSULTING AGREEMENT

This Consulting Agreement (this "Agreement") is made and entered into as of
[DATE] (the "Effective Date"), by and between:

TECHSTART INC, a Delaware corporation with its principal place of business
located at [ADDRESS], California (hereinafter referred to as "Company"),

and

JOHN SMITH, an individual residing in the State of Texas (hereinafter
referred to as "Consultant").

Company and Consultant are sometimes referred to herein individually as a
"Party" and collectively as the "Parties."

                              RECITALS

WHEREAS, Company is engaged in the business of developing and marketing
technology products and services; and

WHEREAS, Consultant possesses expertise and experience in marketing strategy,
go-to-market planning, and brand positioning; and

WHEREAS, Company desires to engage Consultant to provide certain marketing
consulting services, and Consultant desires to provide such services to
Company, subject to the terms and conditions set forth herein;

NOW, THEREFORE, in consideration of the mutual covenants and agreements
hereinafter set forth and for other good and valuable consideration, the
receipt and sufficiency of which are hereby acknowledged, the Parties agree
as follows:

---
### Drafter Notes (Plain English Explanation):
- **What this section does:** This is the opening of the contract. It identifies
  who the parties are and explains why they're entering into this agreement.
  The "WHEREAS" clauses (called "recitals") provide background context.

- **Key provisions:**
  - Both parties are clearly identified with their legal status
  - The "NOW, THEREFORE" paragraph is standard legal language that says
    "because of all the above, here's what we agree to"
  - "Consideration" refers to what each party is giving - here, it's the
    services and payment. This is required for a valid contract.

- **Client decisions needed:**
  - Need to fill in Company's actual California address
  - Confirm the Effective Date when ready to sign

- **State-specific notes:** None for this section

### Ready for Challenge Review: Yes
---
```

**Challenge Agent Review:**

```markdown
---
## CHALLENGE REVIEW: Preamble and Recitals
### Overall Section Risk: Low
---

### Issues Found: 1

#### Issue 1
- **Type:** GAP
- **Text:** "[ADDRESS], California"
- **Problem (Plain English):** The Company address is a placeholder. While you can
  fill this in before signing, having a complete address is important for the
  Notices section (where legal communications get sent).
- **Real-World Impact:** If there's ever a dispute and someone needs to send
  formal notice, they need to know exactly where to send it.
- **Recommendation (Formal Legal Language):** Fill in complete address or ensure
  Section 11 (Notices) includes: "Notices to Company shall be sent to the address
  set forth in the preamble, or such other address as Company may designate in
  writing."
- **Risk Level:** Low

---
### Section Summary
- **Strengths:** Proper formal structure with recitals, clear party identification,
  consideration language included, professional formatting
- **Must Fix:** None
- **Consider Fixing:** Address placeholder
- **Acceptable As-Is:** Can proceed, address is easily filled in later

### Revision Required: No
---
```

**Result:** Section passes. Move to next section.

---

### Section 3: Term and Termination (Example with Issues)

**Contract Drafter Output v1:**

```markdown
---
## SECTION: Term and Termination
### Draft Version: 1
### Risk Level: Medium
---

                            ARTICLE III
                       TERM AND TERMINATION

3.1  Term. This Agreement shall commence on the Effective Date and shall
continue for a period of six (6) months (the "Initial Term"). This Agreement
shall automatically renew for successive six (6) month periods unless either
Party provides notice of non-renewal.

3.2  Termination for Convenience. Either Party may terminate this Agreement
at any time for any reason.

3.3  Termination for Cause. Either Party may terminate this Agreement
immediately if the other Party materially breaches any provision hereof.

3.4  Effect of Termination. Upon termination of this Agreement, Consultant
shall return all Company materials and Company shall pay Consultant for
services rendered.

---
### Drafter Notes (Plain English Explanation):
- **What this section does:** Defines how long the contract lasts and how
  either party can end it.

- **Key provisions:**
  - 6-month initial term with automatic renewals
  - Either party can end it for any reason
  - Immediate termination if someone breaches

- **Client decisions needed:** None at this stage

- **State-specific notes:** None

### Ready for Challenge Review: Yes
---
```

**Challenge Agent Review:**

```markdown
---
## CHALLENGE REVIEW: Term and Termination
### Overall Section Risk: High
---

### Issues Found: 4

#### Issue 1
- **Type:** AMBIGUITY
- **Text:** "unless either Party provides notice of non-renewal"
- **Problem (Plain English):** There's no timeframe for when you need to give
  notice. Someone could technically give notice one day before the renewal
  kicks in, leaving you scrambling.
- **Real-World Impact:** You might find yourself locked into another 6 months
  because you missed an unclear deadline. Or the consultant might leave right
  when you need them most because they only had to give 1 day notice.
- **Recommendation (Formal Legal Language):** "unless either Party provides
  written notice of non-renewal to the other Party at least thirty (30) days
  prior to the expiration of the then-current term"
- **Risk Level:** Medium

#### Issue 2
- **Type:** GAP
- **Text:** "may terminate this Agreement at any time for any reason"
- **Problem (Plain English):** No notice period at all. The consultant could
  walk out in the middle of a critical project. You could cut off their income
  with zero warning.
- **Real-World Impact:** Imagine you're two weeks from a major product launch
  and the consultant just... stops. No transition, no handoff. That's what
  this language allows.
- **Recommendation (Formal Legal Language):** "Either Party may terminate this
  Agreement for any reason or no reason upon thirty (30) days' prior written
  notice to the other Party."
- **Risk Level:** High

#### Issue 3
- **Type:** AMBIGUITY
- **Text:** "materially breaches any provision hereof"
- **Problem (Plain English):** "Material breach" isn't defined. Is being one
  day late on a deliverable material? What about a typo in a report? You and
  the consultant might have very different views.
- **Real-World Impact:** The consultant could claim you "materially breached"
  by paying a day late and try to terminate immediately. Or you could both
  end up in a dispute about whether a breach was "material" enough.
- **Recommendation (Formal Legal Language):** Add specific examples and a cure
  period. See revised Section 3.3 below.
- **Risk Level:** Medium

#### Issue 4
- **Type:** GAP
- **Text:** Section 3.4 Effect of Termination
- **Problem (Plain English):** This section is dangerously incomplete. It doesn't
  address:
  - Who owns work that's partially complete when the contract ends?
  - Does confidentiality survive after termination? (It should!)
  - Is there any transition period to hand things off?
  - What about work product the consultant hasn't delivered yet?
- **Real-World Impact:** Without these provisions, if the contract ends badly,
  you could have a fight over whether you own the half-finished marketing plan,
  whether the consultant can use your trade secrets now that the contract is over,
  and who owes what to whom.
- **Recommendation (Formal Legal Language):** See comprehensive revision below.
- **Risk Level:** High

---
### Section Summary
- **Strengths:** Covers the basic termination scenarios
- **Must Fix:** Issues 2 and 4 (termination notice period, effect of termination)
- **Consider Fixing:** Issues 1 and 3 (renewal notice timing, material breach definition)
- **Acceptable As-Is:** None - this section needs work

### Revision Required: Yes
---
```

**Contract Drafter Output v2:**

```markdown
---
## SECTION: Term and Termination
### Draft Version: 2
### Risk Level: Low
---

                            ARTICLE III
                       TERM AND TERMINATION

3.1  Term. This Agreement shall commence on the Effective Date and shall
continue in full force and effect for a period of six (6) months (the
"Initial Term"), unless earlier terminated in accordance with the provisions
hereof. Upon expiration of the Initial Term, this Agreement shall
automatically renew for successive six (6) month periods (each, a "Renewal
Term" and together with the Initial Term, the "Term"), unless either Party
provides written notice of non-renewal to the other Party at least thirty
(30) days prior to the expiration of the then-current Term.

3.2  Termination for Convenience. Either Party may terminate this Agreement
for any reason or no reason upon thirty (30) days' prior written notice to
the other Party.

3.3  Termination for Cause. Either Party may terminate this Agreement
immediately upon written notice to the other Party if:

     (a)  the other Party fails to pay any amounts due hereunder within
          fifteen (15) days after receipt of written notice of such
          non-payment;

     (b)  the other Party materially breaches any other provision of this
          Agreement and fails to cure such breach within fifteen (15) days
          after receipt of written notice specifying the nature of such
          breach in reasonable detail; or

     (c)  the other Party becomes insolvent, makes an assignment for the
          benefit of creditors, or becomes the subject of any proceeding
          under any bankruptcy or insolvency law which proceeding is not
          dismissed within sixty (60) days.

3.4  Effect of Termination. Upon any expiration or termination of this
Agreement:

     (a)  all rights and licenses granted by Company to Consultant hereunder
          shall immediately terminate, and Consultant shall immediately
          cease performing Services;

     (b)  Consultant shall promptly return to Company, or at Company's
          election destroy and certify in writing such destruction of, all
          Confidential Information and other materials of Company in
          Consultant's possession or control;

     (c)  Company shall pay Consultant for all Services satisfactorily
          rendered through the effective date of termination, such payment
          to be made within thirty (30) days of termination;

     (d)  all Work Product, whether completed or in progress as of the date
          of termination, shall be and remain the sole and exclusive
          property of Company, and Consultant shall deliver all such Work
          Product to Company promptly upon termination;

     (e)  upon Company's request, Consultant shall provide reasonable
          transition assistance for a period not to exceed two (2) weeks
          following termination, such assistance to be compensated at the
          pro-rata rate of the Monthly Retainer; and

     (f)  notwithstanding any expiration or termination of this Agreement,
          the provisions of Article IV (Compensation) with respect to
          amounts accrued prior to termination, Article V (Intellectual
          Property), Article VI (Confidentiality), Article VIII (Limitation
          of Liability), Article IX (Indemnification), and Article X
          (Dispute Resolution) shall survive and continue in full force
          and effect.

---
### Drafter Notes (Plain English Explanation):
- **What this section does:** Completely revamped termination section with proper
  protections for both parties.

- **Key provisions explained in plain English:**
  - **Renewal (3.1):** The contract renews automatically, but either side can stop
    that by giving 30 days notice before the term ends.
  - **Convenience termination (3.2):** Either party can end the contract for any
    reason with 30 days notice. This gives you both time to wrap up.
  - **For cause termination (3.3):** If someone seriously messes up (doesn't pay,
    breaches the contract, goes bankrupt), the other party can end it immediately
    - BUT they have to give written notice and a chance to fix it first (except
    for bankruptcy).
  - **What happens after (3.4):**
    - Consultant stops work and returns all your materials
    - You pay for work done through the end date
    - You own everything created, even if it's half-finished
    - Consultant helps with handoff for up to 2 weeks if you ask
    - Key protections (confidentiality, IP, etc.) continue forever

- **Client decisions needed:** None - this is comprehensive

- **State-specific notes:** Survival provisions are standard and enforceable
  across all US jurisdictions

### Ready for Challenge Review: Yes
---
```

**Challenge Agent Review v2:**

```markdown
---
## CHALLENGE REVIEW: Term and Termination
### Overall Section Risk: Low
---

### Issues Found: 0

### Section Summary
- **Strengths:**
  - Clear notice periods for both renewal and termination for convenience
  - Specific termination events with cure periods
  - Comprehensive effect of termination addressing all major concerns
  - Proper survival clause ensuring key protections continue
  - Transition assistance provision for smooth handoffs
  - Work product ownership explicitly addressed for incomplete work

- **Must Fix:** None
- **Consider Fixing:** None
- **Acceptable As-Is:** This section is now comprehensive and balanced

### Revision Required: No
---
```

**Result:** Section passes. Move to next section.

---

## Phase 3: Scenario Testing (Abbreviated)

After all sections are drafted, run scenarios:

```markdown
## SCENARIO TEST: IC-6 (Work Product Ownership)

### Scenario Description
Six months into the engagement, the relationship sours. Consultant claims IP
rights in the marketing strategy deliverables, saying they're based on his
pre-existing frameworks that he's used with other clients.

### Contract Coverage
- **Addressed:** Yes
- **Relevant Sections:** Article V (Intellectual Property)

### Analysis
Article V, Section 5.2 states:

"Consultant hereby irrevocably assigns to Company all right, title, and interest
in and to any and all Work Product. 'Work Product' means all deliverables,
reports, strategies, plans, analyses, recommendations, and other materials
conceived, created, or developed by Consultant, solely or jointly with others,
in connection with the performance of Services hereunder."

Section 5.3 addresses pre-existing IP:

"Consultant represents and warrants that the Work Product shall not incorporate
any Pre-Existing IP of Consultant without Company's prior written consent. To
the extent any Pre-Existing IP is incorporated into Work Product with Company's
consent, Consultant hereby grants Company a perpetual, irrevocable, worldwide,
royalty-free license to use such Pre-Existing IP solely as incorporated in the
Work Product."

### Verdict
- **Status:** PASS
- **Risk Level:** Low
- **Recommendation:** Scenario is adequately addressed. Consultant's pre-existing
  frameworks either (a) shouldn't be in the deliverables without written consent,
  or (b) if included with consent, Company gets a license.
```

```markdown
## SCENARIO TEST: T-3 (Automatic Renewal Dispute)

### Scenario Description
The contract auto-renewed but Consultant claims they sent a non-renewal notice
by email. Company says they never received it. Now both parties disagree about
whether the contract is still in effect.

### Contract Coverage
- **Addressed:** Partially
- **Relevant Sections:** Section 3.1 (Term), Article XI Section 11.6 (Notices)

### Analysis
Section 3.1 requires "written notice of non-renewal... at least thirty (30)
days prior to the expiration of the then-current Term."

Section 11.6 (Notices) states notices "shall be deemed to have been duly given
when: (a) delivered personally; (b) sent by confirmed email; (c) sent by
nationally recognized overnight courier; or (d) sent by registered or certified
mail, return receipt requested."

**Gap:** "Confirmed email" isn't precisely defined. Does the sender need a read
receipt? Delivery confirmation? What if the email went to spam?

### Verdict
- **Status:** NEEDS WORK
- **Risk Level:** Medium
- **Recommendation (Formal Legal Language):** Add to Section 11.6:

"Email notices shall be deemed 'confirmed' upon (i) receipt of an electronic
delivery confirmation from the recipient's mail server, or (ii) written
acknowledgment of receipt from the recipient. The burden of proving delivery
shall be on the sending Party. In the event of a dispute regarding delivery,
if the sending Party cannot provide reasonable evidence of delivery, the
notice shall be deemed not to have been given."
```

---

## Phase 4: Gap Remediation

Address NEEDS WORK scenario:

**Drafter adds to Article XI, Section 11.6 (Notices):**

```
11.6  Notices. All notices, requests, demands, and other communications
required or permitted under this Agreement shall be in writing and shall be
deemed to have been duly given when: (a) delivered personally; (b) sent by
confirmed email; (c) sent by nationally recognized overnight courier
(e.g., FedEx, UPS); or (d) sent by registered or certified mail, return
receipt requested, postage prepaid.

For purposes of this Section, email notices shall be deemed "confirmed"
upon (i) receipt by the sending Party of an electronic read receipt or
delivery confirmation from the recipient's mail server, or (ii) written
acknowledgment of receipt from the recipient. The sending Party shall
retain evidence of such confirmation. In the absence of such confirmation,
email notice shall be deemed received upon the fifth (5th) Business Day
following the date sent, provided that the sending Party can demonstrate
the email was sent to the correct email address.
```

**Re-run Scenario T-3:** PASS

---

## Phase 5: Final Output

### Risk Score Summary

| Section | Score | Risk Level |
|---------|-------|------------|
| Preamble/Recitals | 3.8 | Low |
| Definitions | 4.0 | Low |
| Scope of Services | 3.5 | Low |
| Term/Termination | 3.8 | Low |
| Compensation | 3.7 | Low |
| Intellectual Property | 4.0 | Low |
| Confidentiality | 3.9 | Low |
| Representations | 3.5 | Low |
| Limitation of Liability | 3.2 | Medium |
| Indemnification | 3.4 | Medium |
| Dispute Resolution | 3.8 | Low |
| General Provisions | 4.0 | Low |

**Overall Score: 3.7 / 4.0**
**Overall Risk Level: LOW RISK CONTRACT**
**Scenario Pass Rate: 95%**

### Generated Contract Preview

The final output would be the complete, formatted contract in formal legal language:

```
                         CONSULTING AGREEMENT

This Consulting Agreement (this "Agreement") is made and entered into as of
January 15, 2025 (the "Effective Date"), by and between:

TECHSTART INC, a Delaware corporation with its principal place of business
located at 123 Innovation Drive, San Francisco, California 94105 (hereinafter
referred to as "Company"),

and

JOHN SMITH, an individual residing in the State of Texas (hereinafter
referred to as "Consultant").

[... full contract continues with all Articles ...]

IN WITNESS WHEREOF, the Parties have executed this Agreement as of the date
first written above.

TECHSTART INC


By: ________________________________
Name:
Title:
Date:


JOHN SMITH


________________________________
Date:
```

### Plain English Summary for Client

> **What you're signing:** A 6-month consulting agreement where John Smith will
> help develop your marketing strategy for $5,000/month.
>
> **Key protections for you:**
> - You own all the work product, even if the relationship ends early
> - Your confidential information is protected forever
> - Non-compete prevents John from working with MarketCo or StrategyPlus
> - You can end the contract with 30 days notice
>
> **Your obligations:**
> - Pay $5,000 at the start of each month
> - Give 30 days notice if you want to end early
> - Provide reasonable access to information John needs
>
> **If something goes wrong:**
> - Disputes go to mediation first, then arbitration if needed
> - California law applies
> - Your maximum exposure is capped (see Limitation of Liability)

### Recommendations

1. Have an attorney review the Limitation of Liability section for California-specific requirements
2. Consider adding D&O or E&O insurance requirements
3. Keep records of deliverable acceptance to support payment obligations
4. Fill in the Company address before signing

### Disclaimer

This contract was generated by AI and should be reviewed by a licensed attorney before signing. This does not constitute legal advice. Laws vary by jurisdiction and specific circumstances may require modifications.
