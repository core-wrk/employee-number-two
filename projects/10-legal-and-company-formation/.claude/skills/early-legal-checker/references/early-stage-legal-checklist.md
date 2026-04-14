# Formation-Era Legal Checklist — Full Reference

**Scope:** US entities only. Items organized by when they come up in a founder's timeline. Each item has a "when this matters" condition — skip items whose conditions don't apply to the founder's situation.

**Not legal advice.** This is a conversation agenda for a qualified attorney, not a substitute for one.

---

## Section 1: At Formation

### BOI (Beneficial Ownership Information) Filing

**What it is:** Federal filing under the Corporate Transparency Act (CTA), administered by FinCEN. Reports beneficial owners (25%+ holders or those exercising substantial control) and company information.

**When this matters:** Required for most entities formed or registered to do business in the US. Exemptions exist for publicly-traded companies, large operating companies (20+ full-time US employees + $5M+ revenue), and certain regulated entities — almost no startups qualify for exemption.

**Deadline:**
- Entities formed in 2024: 90 days from formation
- Entities formed in 2025+: 30 days from formation
- Existing entities formed before 2024 had initial deadlines (January 1, 2025)
- Updates: within 30 days of any change to beneficial ownership

**How to file:** FinCEN BOIR portal (boiefiling.fincen.gov) — self-service, no filing fee.

**Caveat:** The CTA BOI requirement has faced legal challenges and the filing mandate has been in flux. Verify current status with an attorney before assuming it is or isn't required.

**Penalties for non-filing:** Civil penalties up to $500/day; criminal penalties up to $10,000 and 2 years imprisonment for willful violations.

---

### Registered Agent

**What it is:** A person or entity in the state of incorporation designated to receive official correspondence (lawsuits, state notices, tax documents).

**When this matters:** Required in every state of incorporation and in every state where the entity is foreign-qualified.

**Options:**
- Incorporation service (Stripe Atlas, Clerky, Firstbase) typically provides one year included
- Standalone registered agent services: Northwest Registered Agent, Harvard Business Services, InCorp, LegalZoom — $100–$300/year
- Founder can self-serve in their home state if they have a physical address there; not recommended for Delaware entities formed by non-Delaware founders

---

### EIN (Employer Identification Number)

**What it is:** Federal tax ID for the entity, required for bank accounts, hiring, and tax filings.

**When this matters:** Always. Required before opening a business bank account.

**How to file:** IRS Form SS-4, free, online (for applicants with SSN) or fax/mail (for non-US applicants). Online filing issues EIN immediately; fax/mail ~4 weeks.

**Non-US founders:** EIN application from abroad is more cumbersome but doable. Some incorporation services (Stripe Atlas, Firstbase) handle this.

---

### Operating Agreement (LLC) or Bylaws (Corporation)

**What it is:** The document governing internal operations, member/shareholder rights, voting, distributions, and disputes.

**When this matters:** Always. Many states require it even for single-member LLCs.

**Template vs. lawyer:**
- Single-member LLC with no unusual terms: template from incorporation service is usually fine
- Multi-member LLC or corporation: lawyer-drafted, tailored to the specific member/shareholder situation

---

### Initial Board/Member Consent

**What it is:** Documented authorization of the first corporate actions: appointing officers, authorizing stock issuance, opening bank accounts, adopting bylaws.

**When this matters:** Always. Most incorporation services provide templates.

---

## Section 2: Within 30 Days of Equity Issuance (the 83(b) Window)

### 83(b) Election

**What it is:** IRS filing electing to pay tax on the fair market value of restricted stock at the time of issuance rather than as it vests.

**When this matters:** Any time equity is issued subject to vesting — founder shares, co-founder shares, early-employee restricted stock.

**Deadline:** 30 days from the date of issuance. **No extensions. No exceptions.** If missed, the founder will pay tax on the FMV of each vesting tranche at the then-current value. For a company that grows, this is catastrophic — a founder with 1M shares vesting at a $10/share valuation owes ordinary-income tax on $10M in the year of vesting, even though they have not sold anything.

**How to file:**
1. Sign the 83(b) election form (template available from incorporation services or the IRS)
2. Mail to the IRS service center for your state by **certified mail, return receipt requested**
3. Keep the return receipt and a copy of the filed form forever
4. Provide a copy to the company
5. Attach a copy to the founder's personal tax return for the year of issuance

**Common mistakes:**
- Missing the deadline (catastrophic, irreversible)
- Sending by regular mail (no proof of filing — if IRS loses it, founder has no recourse)
- Forgetting to attach to personal tax return (technical issue; filing still valid if sent on time, but creates ambiguity)

---

### Restricted Stock Purchase Agreement (RSPA)

**What it is:** The contract under which founder/co-founder stock is issued subject to vesting and repurchase rights.

**Typical terms:**
- 4-year vesting with 1-year cliff
- Company right to repurchase unvested shares at cost if holder leaves
- Voluntary-termination vs. involuntary-termination buyback provisions
- Transfer restrictions (right of first refusal, prohibited transfers)

**Lawyer required.** Templates exist (Clerky produces good ones; NVCA model forms are widely used) but should be reviewed for the specific founder/co-founder situation. Incorrect vesting design is a common source of co-founder disputes that cost more than a lawyer would have.

---

### PIIA (Proprietary Information and Inventions Assignment)

**What it is:** Agreement under which the founder, employee, or contractor assigns all work-related IP to the company.

**When this matters:** Each founder and each person who contributes code, design, or IP must sign one. Critical at formation; catastrophic if a key contributor leaves without one.

**Lawyer required.** Template available, but California and a few other states have specific carve-outs (California Labor Code 2870 prevents employers from claiming IP developed on the employee's own time with no employer resources and unrelated to the employer's business). State-specific drafting matters.

---

## Section 3: Before Launch

### Terms of Service / Terms of Use

**What it is:** The contract between the company and its users.

**When this matters:** Before any user interacts with the product beyond a marketing page — including a waitlist that collects email addresses.

**Path:**
- **Pre-revenue, pre-launch:** Template from Termly, iubenda, or Rocket Lawyer is usually acceptable. Plan ~$10–$40 for a year of updates.
- **At launch / first real customer:** A lawyer-drafted TOS is worth paying for, especially for B2B SaaS with enterprise customers. Enterprise legal teams review TOS carefully.
- **Regulated industries (healthcare, fintech, children's data):** Always lawyer-drafted, always.

---

### Privacy Policy

**When this matters:** The moment the product collects any user data. This includes waitlist signups, newsletter subscribers, analytics cookies, and embedded third-party tools.

**Path:** Same as TOS. Additional complexity if users are in the EU (GDPR), UK (UK GDPR), or California (CCPA/CPRA). Generator services handle basic multi-jurisdictional compliance; lawyer-drafted is better for regulated data (health, finance, children's).

---

### Cookie Consent and Data Processing

**When this matters:** If collecting any cookies, running analytics, or embedding any third-party tools (HubSpot forms, Calendly, Intercom, etc.).

**Path:**
- Cookie consent banner: generator services or simple libraries (Osano, OneTrust, CookieYes)
- If EU users: GDPR-compliant consent (opt-in, not opt-out; granular by purpose)
- If California users: CCPA "Do Not Sell or Share My Personal Information" link required

---

### Trademark Filing

**What it is:** USPTO registration of a product or company mark.

**When this matters:** Decision point before meaningful brand investment. Not required for formation, but increasingly painful to retrofit after the brand has market presence.

**Process:**
- Pre-filing clearance search (USPTO TESS + web/social/domain search)
- Filing: $250–$350 per class per application
- Attorney assistance: $500–$1,500 for filing support; more for contested prosecution

**Common mistakes:**
- Filing without clearance (someone else has prior rights — filing gets rejected and the fee is lost)
- Filing too narrowly (missed classes leave the brand exposed in adjacent use cases)
- Filing in the individual's name rather than the company's (must be company-owned post-formation)

---

### IP Assignment Verification

**When this matters:** Before launch, before any investor diligence, before any acquisition discussion.

**Purpose:** Confirm that every contributor to the company's IP (code, design, brand, content) has signed an IP assignment. A missing assignment from an early contractor or founder who has since left is one of the most expensive things to fix later.

**How:**
- List every person who has contributed to the codebase, design files, written content, or IP
- Confirm each has a signed PIIA or equivalent in the company's records
- Any gaps → lawyer immediately to draft and obtain retroactive assignments

---

## Section 4: At First Hire

### Offer Letter or Independent Contractor Agreement

**Employee:** Offer letter + at-will acknowledgment + PIIA + employee handbook (or pointer)

**Contractor:** Independent Contractor Agreement — must clearly establish contractor status (1099) rather than employee (W-2). Misclassification penalties are serious.

---

### Stock Option Grant (if issuing options)

**Prerequisites:**
- Stock Plan adopted by the board (ISO or NSO structure)
- Share pool reserved (typical early pool: 10–15% of fully-diluted)
- 409A valuation to set strike price (required for any stock option grant; $500–$2,000 from services like Carta, Pulley, Preferred Return)

**Cannot be DIY.** Stock plans and grant agreements are lawyer work.

---

### Payroll Setup

**Triggers:**
- State payroll tax registration (unemployment insurance, disability, withholding)
- Federal payroll tax registration (via EIN)
- Workers' comp insurance (required in most states for any W-2 employee)
- Benefits decisions (health insurance triggers at certain employee counts; some states require retirement offerings)

**Provider:** Gusto, Rippling, Justworks, Deel — all handle payroll + basic compliance. Pick one; don't DIY payroll.

---

## Section 5: Ongoing Compliance Calendar

### Delaware Entities

- **Franchise tax:** Due March 1 every year. LLC: flat $300. C-Corp: lesser of authorized-shares method or assumed-par-value-capital method (the latter is almost always cheaper if properly calculated; verify with your incorporation service or CPA).
- **Annual report:** Filed with franchise tax return for C-Corps; LLCs do not file annual reports.
- **Registered agent fee:** ~$100–$300/year.

### California Entities

- **Minimum franchise tax:** $800/year (LLC and corporation). First-year exemption for corporations formed after 2020 in some cases.
- **LLC gross receipts fee:** Additional fee on LLCs with California-source gross receipts above $250k; scales with revenue.
- **Statement of Information:** $20 (LLC, biennial) or $25 (corporation, annual). Late filings incur penalties.

### Other States

Vary widely. Texas has franchise tax only on entities with $1.23M+ revenue. Florida has no state income tax and light filings. Consult state-specific guidance or the registered agent.

### Federal

- **Income tax return:** Annual. Form 1120 (C-Corp), 1120-S (S-Corp), 1065 (partnership / multi-member LLC), Schedule C (single-member LLC disregarded entity).
- **Quarterly estimated taxes:** Owners of pass-through entities typically; entities at the entity level for C-Corps.
- **Payroll returns (if employees):** Form 941 quarterly, Form 940 annually, W-2s to employees, 1099s to contractors.

### BOI Updates

Within 30 days of any change to beneficial ownership (new equity holders, departing founders, ownership changes from fundraising).

---

## Section 6: Situational Items

### If Founder Was Previously Employed

IP assignment risk from the prior role. Covered in detail by Project 01's `early-legal-checker`. If that has not been run, flag it and run it before proceeding further.

### If Regulated Industry

Healthcare (HIPAA, potentially state licensing), fintech (state money-transmitter licenses, potentially FinCEN registration), legal services (state bar rules on UPL and non-lawyer ownership), education data (FERPA), children's products (COPPA) — all require lawyer engagement from formation. Do not proceed without one.

### If Non-US Founder

Treaty considerations, ITIN requirements, transfer pricing between the US entity and home-country services, controlled foreign corporation rules in home jurisdiction. US and home-country counsel both required.

### If Co-founder Dispute Potential

Vesting (4-year standard with 1-year cliff), repurchase rights, dispute resolution clauses, founder-departure playbook. These are the most expensive things to retrofit. Invest in lawyer-drafted documents at formation.

---

## Self-Service Items (Legitimately DIY)

- FinCEN BOI filing
- IRS EIN application
- 83(b) filing (following a standard template, certified mail)
- Basic TOS/privacy policy from Termly or iubenda for pre-revenue use
- Registered agent selection (if not bundled with incorporation service)
- Domain registration in company name
- Setting up a compliance calendar in your own calendar tool

## Lawyer-Required Items

- Operating agreements and bylaws for multi-member/multi-shareholder situations
- Restricted Stock Purchase Agreements
- PIIA / Invention Assignment Agreements
- Stock plans and option grant agreements
- Production-grade TOS and Privacy Policy (post-launch or regulated industries)
- Trademark filings (self-service possible but often worth the lawyer)
- Anything in a regulated industry
- Any co-founder situation with non-trivial equity splits or contribution asymmetries
- Anything a VC will diligence (plan for this before the first term sheet)
