# Early-Stage Legal Flags

This is an internal reference for the `early-legal-checker` skill. It organizes common early-stage legal flags by founder situation and by risk category. **Do not show this document to the founder.** Use it to tailor the conversation and to make sure nothing obvious is missed.

**This is not legal content.** It is a list of common patterns that early-stage founders often run into. Nothing in this document should be presented as legal advice, either to the founder directly or via the written report. Everything surfaced here becomes a question for a qualified attorney.

---

## Category 1: IP Assignment Risk

This category matters if the founder is currently employed (full-time, part-time, contract, academic, or any paid role) or was recently employed and left with IP-related clauses still in force.

### Common contractual clauses that create flags

- **Broad invention assignment clauses.** Assigns to the employer any IP created during employment, sometimes broadly enough to cover side projects. Common in tech, biotech, and academia.
- **"Works for hire" clauses.** Similar but frames the output as employer-owned from creation.
- **Duty of disclosure.** Requires the founder to tell the employer about outside work or inventions. Triggering this clause accidentally (by not disclosing) can create problems even if the employer has no claim to the IP itself.
- **Non-compete clauses.** Prevents working on a competing business. Scope varies wildly by jurisdiction — California generally unenforceable, many other US states enforceable, EU highly variable.
- **Non-solicit clauses.** Prevents recruiting employees or customers from the employer. Usually time-bounded.
- **Trade secret and confidentiality clauses.** Prevents using or disclosing employer information. Can overlap uncomfortably with a founder's own pre-existing knowledge.
- **"Tools and time" doctrine.** Some jurisdictions hold that using employer resources (laptop, email, time during working hours) to create IP gives the employer a shop right or ownership claim even absent a specific clause.
- **Prior inventions exclusions.** Most employment agreements have a section where the employee can list prior inventions they are carving out of assignment. Founders who do not list their startup idea before joining a new job can lose the carve-out.

### Situation: Currently employed
Questions to surface in conversation:
- What does the employment agreement say about IP assignment, inventions, side projects?
- Has the founder told the employer about the project? (Disclosure vs. non-disclosure is a real strategic choice and should be informed by legal advice.)
- Is the founder using employer equipment (laptop, phone, cloud accounts, subscriptions)?
- Is the founder working on this during hours the employer considers "work hours"?
- Is the project in the same field as the employer's business?
- When did the founder start thinking about this idea? Before or after joining the employer?

The last question matters because some jurisdictions treat ideas predating employment differently from ideas formed during employment, but only if the founder can document the timeline.

### Situation: Recently left employment (last 12 months)
Questions:
- What clauses from the prior employment agreement were still in force at the time of leaving? (Non-compete, non-solicit, confidentiality, and sometimes IP assignment clauses have tail periods.)
- Is the founder recruiting anyone from the prior employer?
- Is the founder targeting customers from the prior employer?
- Is the founder using any materials (documents, data, code) from the prior employer?

### Situation: Academic affiliation
Universities frequently have very broad IP assignment policies. Even part-time teaching, research fellowship, or PhD candidacy can trigger IP assignment to the university.
- Does the founder's institution have a technology transfer office?
- What does the institution's IP policy say about student / faculty inventions?
- Does the institution have a founder-friendly policy (some do, most do not)?

### Situation: Independent contractor to a past client
- What did the contractor agreement say about IP? (Sometimes broadly written, sometimes narrowly tied to the specific project.)
- Is the founder building something in the same space as the client?
- Did the contractor agreement have any ongoing non-compete or confidentiality provisions?

### Situation: Truly unemployed / no prior employment conflicts
Usually clean. Skip quickly and move on. But ask if there are any old agreements (previous startups, co-founded projects, advisory positions) that might still be relevant.

---

## Category 2: Design-Partner Confidentiality

This applies to every founder, regardless of employment status, as soon as they start having conversations with potential customers about the product.

### Common patterns

**Asking everyone to sign an NDA.** Kills conversation pace, signals distrust, and is usually unnecessary for early discovery conversations where the founder is learning rather than revealing. Strongly discouraged by most startup-focused attorneys for this stage.

**Never using NDAs.** Fine for discovery conversations but becomes a problem when:
- A potential customer shares genuinely sensitive information (internal processes, data samples, strategic plans)
- The founder begins sharing material product details that have competitive value
- The relationship evolves from "curious prospect" to "active design partner"

**One-sided NDAs.** Founder-protective only, asking the customer to protect the founder's information but not vice versa. Customers often find this off-putting; mutual NDAs are more common.

**Mutual NDAs.** Both parties agree to protect each other's information. Standard for design-partner relationships once they become serious.

### Flags to surface

- Does the founder have a mental model for when to use NDAs and when not to?
- Is the founder about to share something (product architecture, pricing, customer names) they would not want public?
- Is the founder about to receive something (customer data samples, internal documents, strategic plans) that the customer would not want shared?
- Does the founder have a template or plan for how to ask? (Sending a 15-page enterprise NDA is very different from sending a one-page mutual NDA.)

### Situation: Founder is about to start design-partner conversations
This is the most common trigger for this category. Good questions for an attorney:
- What is a reasonable lightweight NDA template for early design-partner conversations?
- At what point in a design-partner relationship does a more formal agreement become appropriate?
- How should the founder handle being asked to sign an NDA that is broader than expected?

### Situation: Founder has already had many conversations without NDAs
Usually fine — discovery conversations rarely create legal exposure — but ask:
- Was any customer information shared that the customer might consider confidential?
- Did the founder take notes or recordings of those conversations?
- Were there any verbal commitments made about confidentiality?

---

## Category 3: Data Privacy

This applies the moment the founder collects any information from any user — including a waitlist, newsletter signup, beta tester form, or contact form.

### Common regulations

- **GDPR (EU) / UK GDPR.** Triggers when collecting data from EU or UK residents, regardless of where the founder is located. Requires a privacy policy, lawful basis for processing, subject access rights, and more. Financial penalties are real.
- **CCPA / CPRA (California).** Similar scope, California residents. Slightly different requirements than GDPR but overlapping.
- **PIPEDA (Canada), LGPD (Brazil), other jurisdictions.** Similar frameworks, growing list.
- **HIPAA (US, healthcare).** Protected health information. Triggers very different obligations and is much more expensive to comply with.
- **FERPA (US, education).** Student records. Triggers for edtech products.
- **COPPA (US, children under 13).** Dramatically different rules, very expensive to comply with incorrectly.
- **PCI-DSS (payment cards).** Triggers for anything handling credit card numbers.
- **GLBA (US, financial).** Nonpublic personal information from financial institutions.

### Common founder patterns that create flags

**Starting a waitlist with a Google Form or Typeform and no privacy policy.** Very common. Fixable in an hour: add a one-paragraph privacy notice and link to a privacy policy page.

**Using Mailchimp or HubSpot without configuring the data-region settings.** Matters for GDPR.

**Collecting analytics via Google Analytics without consent banners in EU jurisdictions.** Common flag, easy to fix.

**Storing waitlist data in a personal Google Sheet with link-sharing enabled.** A data security issue even before it is a privacy issue.

**Building in a regulated domain without realizing it.** A founder building "a tool for therapists" may not realize they are in the HIPAA domain until they start onboarding actual therapists.

### Flags to surface

- Is any user data being collected anywhere? (Waitlist, contact form, newsletter, analytics, cookies, etc.)
- Where is that data stored?
- Who has access?
- Is there a privacy policy?
- Is there a consent mechanism at the point of collection?
- Are EU, UK, or California users being collected from?
- Is the product domain regulated?

### Situation: Product has a waitlist or contact form
The most common trigger. Usually fixable in a few hours of work with a privacy-policy template and a consent checkbox. Good questions for an attorney:
- What is a minimal, compliant privacy policy for a pre-launch waitlist?
- What consent language is required for the jurisdictions where users might be located?
- Where should the data be stored for minimum exposure?

### Situation: Product is in a regulated domain (health, finance, education, children's data)
Much more serious. The founder should talk to an attorney specifically experienced in the relevant regulation before they collect any data at all. Do not minimize this.

### Situation: Product is consumer-facing at scale
If the founder is planning a public launch to consumers (not a B2B early-access situation), jurisdiction becomes very broad very quickly. Flag the need for a proper privacy policy, cookie consent, and data-handling review well before launch.

---

## Cross-Cutting Flags

A few flags do not fit neatly into one category but are worth surfacing:

### Founder is already using a company name
- Has the name been checked for trademark conflicts? (See `naming-validator` skill.)
- Has any entity been incorporated yet, and if so in what state and as what type? (See Project 10.)
- Is the domain registered to the founder personally or to a company that does not exist yet?

### Founder has a co-founder
- Is there a written agreement between the co-founders about equity split, vesting, roles, and IP ownership?
- If not, the single biggest flag in this category: "You should have a co-founder agreement in writing before you do anything else that creates value." This is one of the most common early-stage disasters and one of the cheapest to prevent.

### Founder has taken any money from anyone
- Friends and family investment without documentation is a common flag.
- Accelerator participation usually comes with its own agreements that should be reviewed.
- Any "we'll figure out equity later" arrangement with early contributors is a flag.

These cross-cutting flags should be mentioned briefly in the report's "Recommended Next Actions" section even if they did not come up in the main three-category walk.

---

## Tone Calibration

The goal of this skill is to make the founder *aware* of flags, not *anxious* about them. Calibration rules:

- **"This is common and usually cheap to address early"** — say this often. Most flags here are solvable in a few hours of attorney time if caught early.
- **"This one is more serious, and I would not recommend moving further until you talk to a lawyer"** — only for the small number of flags that really warrant it (active IP assignment conflict with current employer, regulated domain with data already being collected, co-founder situation with no agreement and significant equity implications).
- **Avoid alarming language** like "you could be sued," "legal disaster," "massive liability." These are true in theory and almost always misleading in practice for early-stage founders.
- **Do not ever say "you are fine"** — that is a legal conclusion. Say "this is one to mention to your attorney" instead.

The founder should walk away from this conversation with a short, specific list of questions for a lawyer and the calm confidence that most of the flags are standard issues that lawyers handle routinely.
