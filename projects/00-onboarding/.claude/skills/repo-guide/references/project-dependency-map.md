# Project Dependency Map

This reference describes the relationships between projects, what each produces, and what each requires as input. Used by the `repo-guide` skill to answer questions about project ordering and dependencies.

---

## Project Details

### 00 — Onboarding
**Produces:** `founder-profile.md`, `startup-hypothesis.md`
**Requires:** Nothing — this is the starting point
**Estimated effort:** 1 session (30-60 minutes)
**Summary:** Sets up the founder's profile and articulates their startup hypothesis through guided conversation. Every subsequent project reads one or both of these files.

---

### 01 — Market Research
**Produces:** Market sizing report, competitive landscape analysis, customer interview guides, research synthesis
**Writes to global context:** `competitive-landscape.md`, `icp.md` (initial draft)
**Requires:** `founder-profile.md`, `startup-hypothesis.md`
**Estimated effort:** 2-4 sessions
**Summary:** Validates (or challenges) the startup hypothesis with structured research. Outputs a competitive landscape map and a first draft of the ideal customer profile.

---

### 02 — Brand and Marketing
**Produces:** Brand positioning document, messaging framework, brand voice guide
**Writes to global context:** `brand-voice.md`
**Requires:** `founder-profile.md`, `startup-hypothesis.md`, `competitive-landscape.md`, `icp.md`
**Estimated effort:** 1-2 sessions
**Summary:** Defines how the startup talks about itself — positioning, messaging pillars, and voice/tone. Outputs the brand voice guide used by all content-producing projects.

---

### 03 — Brand Identity
**Produces:** Visual identity direction (colors, typography, logo guidance, design principles)
**Writes to global context:** `brand-identity.md`
**Requires:** `brand-voice.md`, `icp.md`
**Estimated effort:** 1-2 sessions
**Summary:** Translates brand voice into visual direction. Does not produce final design assets — it produces a brief that a designer can execute against.

---

### 04 — Inbound Marketing
**Produces:** Content strategy, editorial calendar, waitlist page copy, SEO keyword map, social media templates
**Requires:** `brand-voice.md`, `icp.md`, `competitive-landscape.md`
**Optional:** `brand-identity.md`
**Estimated effort:** 2-3 sessions
**Summary:** Builds the content engine — what to write, where to publish, and how to capture early interest through a waitlist.

---

### 05 — Outbound Sales
**Produces:** Prospect lists, qualification frameworks, outreach sequences, objection handling guides
**Requires:** `icp.md`, `brand-voice.md`, `competitive-landscape.md`
**Optional:** `product-overview.md`
**Estimated effort:** 2-3 sessions
**Summary:** Builds the outbound engine — identifying prospects, qualifying leads, and crafting outreach that reflects the brand voice.

---

### 06 — Product Management
**Produces:** Product requirements document (PRD), feature prioritization matrix, user stories, roadmap
**Writes to global context:** `product-overview.md`
**Requires:** `startup-hypothesis.md`, `icp.md`, `competitive-landscape.md`
**Optional:** Research outputs from 01, feedback from 08
**Estimated effort:** 2-4 sessions
**Summary:** Translates the hypothesis and research into concrete product requirements. Outputs a PRD and writes the product overview to global context.

---

### 07 — Product Development
**Produces:** Technical specifications, architecture decisions, QA test plans, UX review checklists
**Requires:** `product-overview.md` (PRD from 06)
**Estimated effort:** 2-4 sessions
**Summary:** Takes the PRD and produces engineering-ready specifications. Includes QA and UX review frameworks.

---

### 08 — Beta and User Testing
**Produces:** Beta recruitment plan, feedback collection templates, user testing scripts, iteration summaries
**Requires:** `product-overview.md`, `icp.md`
**Estimated effort:** 2-3 sessions (plus ongoing as beta runs)
**Summary:** Plans and structures the beta testing phase — who to recruit, how to collect feedback, and how to synthesize findings into product iterations.

---

### 09 — Pricing and Packaging
**Produces:** Pricing model analysis, packaging options, competitive pricing comparison, pricing page copy
**Writes to global context:** `pricing-model.md`
**Requires:** `product-overview.md`, `icp.md`, `competitive-landscape.md`
**Estimated effort:** 1-2 sessions
**Summary:** Develops and validates the pricing model through competitive analysis, value-based pricing frameworks, and packaging decisions.

---

### 10 — Legal and Company Formation
**Produces:** Entity selection analysis, incorporation checklist, domain/brand protection plan, banking setup guide
**Writes to global context:** `company-profile.md`
**Requires:** `founder-profile.md`
**Optional:** `pricing-model.md` (for tax/structure considerations)
**Estimated effort:** 1-2 sessions
**Summary:** Covers early legal decisions — entity type, state of incorporation, domain registration, and banking. Does not provide legal advice but surfaces the decisions that need to be made and suggests when to engage a lawyer.

---

### 11 — Fundraising Prep
**Produces:** Investor targeting list, pitch deck narrative, advisor recruitment strategy, due diligence preparation
**Requires:** `founder-profile.md`, `startup-hypothesis.md`, `competitive-landscape.md`, `product-overview.md`
**Optional:** `pricing-model.md`, `company-profile.md`
**Estimated effort:** 3-5 sessions
**Summary:** Prepares for fundraising — identifies target investors, crafts the pitch narrative, and organizes materials for due diligence.

---

### 12 — Financial Modeling
**Produces:** Revenue model, cost structure, unit economics analysis, runway projections, scenario planning
**Requires:** `pricing-model.md`, `icp.md`, `product-overview.md`
**Optional:** `company-profile.md`
**Estimated effort:** 2-3 sessions
**Summary:** Builds financial models — revenue projections, cost structures, unit economics, and runway analysis. Produces artifacts that feed directly into pitch materials.

---

## Dependency Summary

```
00 Onboarding
├── 01 Market Research
│   ├── 02 Brand and Marketing
│   │   ├── 03 Brand Identity
│   │   ├── 04 Inbound Marketing
│   │   └── 05 Outbound Sales
│   ├── 06 Product Management
│   │   ├── 07 Product Development
│   │   ├── 08 Beta and User Testing
│   │   └── 09 Pricing and Packaging
│   │       └── 12 Financial Modeling
│   └── 11 Fundraising Prep
└── 10 Legal and Company Formation
```

## Skip Rules

- **00 is always required.** Every project depends on it.
- **01 is strongly recommended.** Most projects depend on its outputs. A founder who has already done extensive market research can fill in `competitive-landscape.md` and `icp.md` manually and skip ahead.
- **02 and 03 can be skipped** if the founder already has brand guidelines.
- **04 and 05 are independent of each other** and can be done in either order.
- **06 should come before 07 and 08** — the PRD drives both engineering specs and beta planning.
- **09 can be done any time after 06** — it needs the product definition but not the engineering specs.
- **10 can be done any time after 00** — it only needs the founder profile.
- **11 and 12 are typically done last** but can be started earlier if fundraising is urgent.
