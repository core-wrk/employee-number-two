# Incorporation Services — Overview

**Scope:** US incorporation service providers. Once the founder has selected an entity structure, this is the menu of ways to actually file the paperwork. This reference is about execution mechanics, not structural choice — the entity decision should already be made before consulting it.

**Not legal advice.** Services listed here are not endorsements; they are the most commonly used options with their tradeoffs. For any non-trivial situation (multiple founders, regulated industry, international founder, custom equity terms), a lawyer is usually a better first call than a service.

---

## Stripe Atlas

**What it does:** Forms a Delaware C-Corp (the primary product) or Delaware LLC. Includes EIN application, Stripe account setup, basic tax guidance, and a simple set of incorporation documents (certificate of incorporation, bylaws, board consent to issue founder stock).

**Cost:** ~$500 flat fee + $250 for LLC ($500 all-in covers C-Corp filing, registered agent for 1 year, document package). State fees separate but baked in.

**Turnaround:** 1–2 weeks for filing; Stripe account usually active before filing completes.

**Best for:**
- Single-founder or 2-founder Delaware C-Corp with vanilla terms (equal equity splits, standard vesting)
- Founders outside the US who need a US C-Corp and banking (Atlas handles both)
- Founders who want "just get me to a working entity quickly" without lawyer friction

**Not great for:**
- Custom equity structures (unusual splits, advisor grants at formation, convertible note already in hand)
- Any situation where the operating agreement or bylaws need customization
- LLCs in states other than Delaware
- Anyone forming in California, Texas, or another high-tax state and wanting to avoid Delaware foreign qualification costs

**Watch out for:** The default Delaware franchise tax method (authorized shares) can produce surprising bills if the company authorizes too many shares (e.g., 10M authorized shares can trigger an $85k+ franchise tax bill unless the founder correctly files using the assumed par value capital method). Atlas usually sets authorized share count sensibly but verify post-filing.

---

## Clerky

**What it does:** Startup-focused legal-document platform. Forms Delaware C-Corps with lawyer-quality documents, handles founder stock issuance with 83(b) filings, supports SAFE issuance, supports priced rounds with proper board consents and stock purchase agreements.

**Cost:** ~$425 for basic incorporation + Delaware fees; higher for the full startup package (stock issuance, founder restricted stock agreements, 83(b) filing support).

**Turnaround:** 2–5 business days for state filing.

**Best for:**
- Multiple founders with real equity dynamics (different splits, vesting schedules, advisor shares)
- Founders who expect to raise and want documents that will survive VC legal diligence without rework
- Founders comfortable reading legal docs — Clerky assumes you can self-serve with well-designed templates

**Not great for:**
- LLCs (Clerky is C-Corp focused)
- Non-US founders without a lawyer (tax complexity isn't handled)
- Founders who want an assistant to fill out forms for them — Clerky is self-serve

**Why VCs prefer it:** Clerky's templates are NVCA-derived and pass diligence cleanly. Stripe Atlas documents are fine but sometimes require minor cleanup at the Series A.

---

## Firstbase

**What it does:** Delaware C-Corp or LLC formation with explicit international-founder support. Includes EIN, US business address, registered agent, and banking-setup assistance.

**Cost:** ~$399 one-time + ongoing registered agent and compliance fees.

**Turnaround:** 1–3 weeks.

**Best for:**
- Non-US founders forming a US entity who need address, EIN, and banking as part of the package
- Founders who want a registered agent subscription and compliance reminders bundled

**Not great for:**
- US-resident founders (Atlas or Clerky usually fit better)
- Complex multi-founder equity situations (Firstbase is formation-focused, not equity-structure-focused)

---

## LegalZoom

**What it does:** Forms LLCs, C-Corps, S-Corps in any US state. Broad service; generic templates.

**Cost:** Base LLC filing from ~$0 + state fees; most founders end up at $200–$500 after common add-ons (operating agreement template, registered agent, EIN support).

**Turnaround:** Varies by state and service tier.

**Best for:**
- Simple single-member LLCs in home state for bootstrapped small businesses
- Situations where the founder genuinely wants a low-cost filing and does not need startup-specific document quality

**Not great for:**
- Any C-Corp intended to raise institutional capital (documents are generic and will need replacement at Series A)
- Founder stock issuance with 83(b) (LegalZoom does not handle this well)
- Complex co-founder dynamics

**Caveat:** LegalZoom upsells aggressively. The base filing is cheap; the full package to get a usable entity with operating agreement and ongoing compliance can reach $500+/year.

---

## Direct-to-State Filing

**What it does:** Founder files directly with the Secretary of State (Delaware, California, etc.) using the state's online portal.

**Cost:** State fees only ($90 in Delaware for LLC or C-Corp + $50 for name reservation if desired; ~$70 in California for LLC; varies elsewhere).

**Turnaround:** Same-day to 1 week depending on state and service level.

**Best for:**
- Experienced founders who have done this before
- Founders forming simple single-member LLCs in home state with no equity complexity
- Cost-sensitive situations where the founder is comfortable sourcing or writing their own operating agreement

**Not great for:**
- First-time founders (no hand-holding, no templates, no EIN assistance — you're on your own)
- Delaware C-Corp for startups (the filing is one small piece; you still need bylaws, stock ledger, board consents, 83(b) filings)

---

## Lawyer-Led Formation

**What it does:** Hire an attorney (typically a startup-focused boutique or a firm like Cooley, WilmerHale, Latham, Orrick, or Gunderson at the high end) to handle formation, founder equity, and early legal docs.

**Cost:** $3,000–$10,000+ for formation work depending on complexity. Some firms offer reduced fees for early-stage startups in exchange for expectation of future work.

**Turnaround:** 2–6 weeks depending on firm and complexity.

**Best for:**
- Multi-founder situations with unequal contributions, IP contributions, or complex equity terms
- Regulated industries
- Founders anticipating a priced seed round or Series A within 12 months (lawyer-led formation produces documents that will not need rework)
- Situations where the founder's time is genuinely better spent building than filing

**Not great for:**
- Tight-budget pre-revenue solo founders with vanilla needs — a lawyer-led formation for a simple Delaware C-Corp is often overkill

**How to find a good startup lawyer:** Ask other founders in your network who they use. Startup-focused boutiques often have flat-fee formation packages for early-stage companies. If you're connected to any VCs, their portfolio-facing lawyer lists are often high-quality referrals.

---

## Decision Framework

| Situation | Recommended path |
|---|---|
| Solo bootstrapped, LLC in home state, simple | Direct-to-state filing, or LegalZoom if you want guidance |
| Solo VC-bound, Delaware C-Corp | Stripe Atlas |
| Two+ founders, VC-bound, standard equity | Clerky |
| Two+ founders, VC-bound, complex equity or IP contributions | Lawyer-led |
| Non-US founder forming US entity | Stripe Atlas or Firstbase |
| Regulated industry | Lawyer-led |
| Already have a term sheet in hand | Lawyer-led (the firm leading the round usually wants to structure formation) |

---

## What None of These Services Do Well

All of these services execute the filing. None of them replace a conversation with a qualified attorney for:

- Operating agreements with real teeth (succession, buyout, dispute resolution)
- Founder IP assignment agreements that hold up if a founder leaves
- Advisor agreements and equity grants
- Any state-specific compliance beyond the initial filing
- Tax strategy (QSBS planning, S-Corp vs. LLC for your specific income, multi-state sales tax)
- Regulated industry licensing

Use a service for the paperwork mechanics. Use a lawyer for the judgment calls. The cost of a lawyer for a 1-hour consultation ($300–$600) is trivial relative to the downside of getting a founder agreement wrong.
