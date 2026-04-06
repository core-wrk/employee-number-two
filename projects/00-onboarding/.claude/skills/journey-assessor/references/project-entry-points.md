# Project Entry Points

Internal reference for the `journey-assessor` skill. Maps founder stages to recommended starting projects and skippable projects.

---

## Stage 1: Idea Stage

**Description:** The founder has a concept but has not validated it with potential customers. They may have domain expertise or personal experience with the problem, but they have not systematically tested their assumptions.

**Start at:** Project 00 (Onboarding)

**Recommended sequence:** 00 → 01 → 02 → then follow natural order

**Skip:** Nothing — work through the full sequence.

**Context files to create:** None needed upfront — projects will create them.

---

## Stage 2: Validated Problem

**Description:** The founder has talked to potential customers and confirmed the problem is real. They have a clear sense of who the customer is and what pain they experience. They may not yet have a solution defined.

**Start at:** Project 02 (Brand and Marketing) or Project 06 (Product Management)

- Start at 02 if they need positioning and brand before building
- Start at 06 if they want to go straight to product definition

**Can skip:** 00 (if profile and hypothesis are filled in), 01 (if they can backfill competitive landscape and ICP)

**Context files to backfill:**
- `founder-profile.md` — required
- `startup-hypothesis.md` — required
- `competitive-landscape.md` — required if skipping 01
- `icp.md` — required if skipping 01

---

## Stage 3: Building

**Description:** The founder has a product in active development. They have a defined solution and are working toward a usable version. They may have early beta users or a waitlist.

**Start at:** Project 07 (Product Development) or Project 08 (Beta and User Testing)

- Start at 07 if they need to formalize specs, QA, or UX review
- Start at 08 if the product is nearly ready for beta users

**Can skip:** 00-06 (with backfilling)

**Context files to backfill:**
- `founder-profile.md` — required
- `startup-hypothesis.md` — required
- `competitive-landscape.md` — recommended
- `icp.md` — required
- `brand-voice.md` — recommended if they have brand guidelines
- `product-overview.md` — required

---

## Stage 4: Live Product

**Description:** The founder has a product that people are using. They may have paying customers or active free users. They are past the building phase and into iteration and growth.

**Start at:** Project 08 (Beta and User Testing), 09 (Pricing), or 11 (Fundraising Prep)

- Start at 08 if they need to structure their feedback and iteration process
- Start at 09 if pricing is the immediate priority
- Start at 11 if fundraising is imminent

**Can skip:** 00-07 (with backfilling)

**Context files to backfill:**
- `founder-profile.md` — required
- `startup-hypothesis.md` — required
- `competitive-landscape.md` — required
- `icp.md` — required
- `product-overview.md` — required
- `brand-voice.md` — recommended
- `pricing-model.md` — required if skipping 09

---

## Stage 5: Scaling

**Description:** The founder has product-market fit signals — retention, revenue growth, organic demand. They are focused on scaling the business, raising capital, or both.

**Start at:** Project 09 (Pricing), 11 (Fundraising Prep), or 12 (Financial Modeling)

**Can skip:** 00-08 (with backfilling)

**Context files to backfill:**
- All global context files should be filled in
- Priority: `founder-profile.md`, `startup-hypothesis.md`, `product-overview.md`, `icp.md`, `competitive-landscape.md`, `pricing-model.md`

---

## General Rules

1. **Always backfill `founder-profile.md` and `startup-hypothesis.md`** regardless of stage. Every project reads at least one of these.
2. **Backfilling is not optional for skipped projects.** If a project is skipped, its output context files must be created manually or the downstream projects will lack critical context.
3. **The founder can always go back.** Skipping a project does not lock them out. If they realize they need market research after starting product development, they can do Project 01 at any time.
4. **Recommend the earliest relevant project, not the latest.** It is better to do slightly more preparation than to skip too far ahead and lack context.
