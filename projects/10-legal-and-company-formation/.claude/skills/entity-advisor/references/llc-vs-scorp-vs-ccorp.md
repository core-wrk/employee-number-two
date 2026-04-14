# LLC vs. S-Corp vs. C-Corp — Entity Structure Reference

**Scope:** US entities only. This reference covers LLC (single-member and multi-member), S-Corp election (on an underlying LLC or corporation), and C-Corp. It does not cover B-Corps (a marketing designation, not a tax structure), non-profits, professional corporations (PCs/PLLCs — consult a lawyer in your state), or sole proprietorships / general partnerships (no liability shield, almost never the right choice for a startup).

**Not legal advice.** This reference exists to inform a conversation with a qualified attorney, not to replace one.

---

## Quick Decision Matrix

| If this is true... | Default structure |
|---|---|
| Planning to raise institutional capital in 12–24 months | Delaware C-Corp |
| Bootstrapped, solo, low revenue, simple operations | Single-member LLC in home state |
| Bootstrapped, profitable, revenue > $80k/yr with low costs | LLC with S-Corp election |
| Multiple co-founders, not fundraising, want operational flexibility | Multi-member LLC |
| Multiple co-founders, will fundraise | Delaware C-Corp |
| Regulated industry (healthcare, fintech, legal services) | Talk to a lawyer first — licensing may constrain structure |
| Non-US founder with US business | Consult counsel; Delaware C-Corp via Stripe Atlas is common but not universal |

This is a starting point, not a conclusion. Every row has edge cases.

---

## LLC (Single-Member and Multi-Member)

### What it is

A limited liability company — a pass-through entity for federal tax purposes (single-member LLCs are "disregarded entities"; multi-member LLCs default to partnership taxation). State-level treatment varies. The LLC shields personal assets from business liabilities if corporate formalities are maintained.

### Tax treatment

- **Single-member LLC:** "Disregarded entity" federally. Profits and losses flow to the owner's Schedule C. All net income is subject to self-employment tax (15.3% on the first ~$168,600 in 2024 for Social Security; Medicare continues without cap).
- **Multi-member LLC:** Files Form 1065 (partnership return). Members receive K-1s. Self-employment tax applies to active members' shares of ordinary income.
- **Either can elect S-Corp or C-Corp taxation** by filing Form 8832 (check-the-box) and for S-Corp, also Form 2553.

### Liability

Personal assets are shielded from business debts and lawsuits *if* corporate formalities are maintained: separate bank account, no commingling, operating agreement, documented decisions. A single-member LLC is more vulnerable to "piercing the corporate veil" than a multi-member LLC in some jurisdictions because courts sometimes treat it as an alter ego of the owner.

### Fundraising compatibility

**Weak for institutional capital.** VCs generally cannot invest in LLCs for tax reasons — pass-through taxation means VC LPs (often tax-exempt entities like endowments and pension funds) would receive UBTI (Unrelated Business Taxable Income). Some angels and rolling funds will invest in LLCs, but most institutional funds require a C-Corp.

**Conversion to C-Corp is possible** but adds cost and complexity: tax implications for existing members, need to issue new stock, potential state-level transfer taxes. Plan ~$5k–$15k in legal and filing fees if conversion happens during a priced round.

### Equity mechanics

LLCs use "membership interests" rather than stock. Can issue "profits interests" (a tax-efficient way to grant equity in an LLC), but traditional stock options do not map cleanly. This makes employee equity harder to administer than in a C-Corp.

### Compliance burden

**Low to moderate.** Annual state filings (varies by state — California $800 minimum franchise tax regardless of revenue; Delaware has a $300 annual franchise tax for LLCs; many states are lower). Operating agreement needed even for single-member LLCs (and many states require it). No separate payroll filings unless employees hired.

### State-of-incorporation question

**Generally form in your home state**, not Delaware, for LLCs. If you form a Delaware LLC but operate in California, you have to register as a foreign LLC in California — you pay both Delaware's franchise tax and California's $800 — and you don't get meaningful benefits for the extra cost. The "form in Delaware" advice comes from the C-Corp world and does not map to LLCs cleanly.

**Exception:** multi-member LLCs with members in multiple states sometimes benefit from Delaware's well-developed LLC case law. Discuss with counsel.

---

## S-Corp Election (on LLC or Corporation)

### What it is

Not an entity — a **tax election** made by filing Form 2553 with the IRS. The underlying entity is an LLC or corporation; S-Corp election changes how it is taxed. Profits still pass through to owners (no double taxation), but the owner can split compensation into a reasonable salary (subject to payroll taxes) and distributions (not subject to self-employment tax), potentially saving on self-employment tax.

### When it makes sense

When net business income exceeds ~$80k/year and you can pay yourself a "reasonable salary" that is meaningfully below total earnings, the self-employment tax savings on distributions above salary can exceed the cost of payroll administration and increased complexity.

Below ~$60k/year, S-Corp election usually costs more than it saves.

### Requirements and constraints

- Maximum 100 shareholders
- All shareholders must be US citizens/residents or certain trusts (no foreign owners, no corporate owners)
- Only one class of stock (makes preferred-stock fundraising impossible — this is why VCs won't invest in S-Corps)
- Must pay owner-employees a "reasonable salary" (IRS scrutinizes this; too-low salary is a frequent audit trigger)

### Compliance burden

**Higher than plain LLC.** Requires: payroll processing (quarterly 941s, annual W-2s, state payroll filings), separate corporate tax return (1120-S), annual minutes and corporate formalities if on a corporation chassis. Plan ~$1,500–$3,000/year in added bookkeeping and payroll service costs.

### Fundraising compatibility

**Incompatible with VC funding.** The single-class-of-stock restriction rules out preferred-stock rounds. Convertible notes may work, but priced rounds typically require revoking the S-Corp election and converting to C-Corp.

### Conversion risk

Revoking S-Corp election to become a C-Corp is straightforward. But going the other way — C-Corp to S-Corp — triggers a 5-year "built-in gains tax" lookback and is rarely worth the complexity.

---

## C-Corporation

### What it is

A separate legal entity taxed at the corporate level under Subchapter C of the Internal Revenue Code. "Double taxation" in the sense that the corporation pays tax on profits, and shareholders pay tax again on dividends — but at the startup stage this usually doesn't matter because startups rarely pay dividends.

### Tax treatment

- Federal corporate rate: flat 21% (post-TCJA)
- State corporate rates vary (Delaware: 8.7% on Delaware-source income, but most SaaS startups have no Delaware source income; California: 8.84%)
- Losses do not pass through to shareholders — they stay with the corporation as Net Operating Losses (NOLs) to offset future profits
- This is a structural disadvantage for unprofitable early-stage companies if the founder has significant W-2 income and wants to offset it with business losses (they cannot, with a C-Corp)

### QSBS — the big upside

Section 1202 Qualified Small Business Stock allows C-Corp stock held for 5+ years to be sold with up to $10M (or 10x basis, whichever is greater) of gain excluded from federal tax. This is the single largest tax break available to startup founders and only applies to C-Corps.

This alone is why VC-bound founders choose C-Corp: a founder who sells a company for $20M after holding founder stock for 5 years can exclude $10M of gain from federal tax, saving ~$2.4M. Pass-through entities do not qualify.

### Fundraising compatibility

**Strong.** The preferred-stock structure VCs require, the unlimited shareholder count, the ability to issue international and corporate shareholders, the QSBS treatment — all align with institutional fundraising. Delaware C-Corp is the de facto standard.

### Equity mechanics

**Strong.** Stock options (ISOs and NSOs), restricted stock, RSUs, preferred stock with various rights — all native to the C-Corp. Employee equity is well-trod territory with established templates (Carta, Pulley, standard legal docs from NVCA).

### Compliance burden

**Moderate to high.** Annual Delaware franchise tax (method matters — authorized shares method can be surprising, assumed par value capital is usually cheaper; a 10M-share C-Corp can owe $85k+ under the default method if not careful). Annual report in state of incorporation, foreign qualification fees in states of operation, corporate tax returns (1120), payroll if employees, minutes and board resolutions for material decisions.

### State-of-incorporation question

**Delaware is the default.** VCs expect Delaware; the Delaware Court of Chancery has the most developed corporate case law; Delaware-specific forms and templates exist everywhere. Forming in your home state as a C-Corp usually means re-incorporating in Delaware before your first priced round anyway, which costs money and time.

**Exception:** If you are absolutely certain you will never raise institutional capital and will stay a small operating company, home-state C-Corp can save on foreign-qualification fees. Rare.

---

## The 83(b) Election

If any equity is being issued at formation — including founder shares — the 83(b) election becomes immediately relevant.

- **What it is:** An IRS filing that elects to pay tax on the value of restricted stock at the time of issuance rather than as it vests. At formation, founder shares are typically worth nominal amounts (e.g., $0.0001/share), so the tax due is tiny.
- **Why it matters:** If you do NOT file, tax is due as each tranche vests, at the then-current fair market value. If the company grows, this can become catastrophic — a founder with 1M shares vesting at a $10/share valuation owes tax on $10M of ordinary income in the year of vesting, even though they have not sold anything.
- **Deadline:** **30 days from the date of stock issuance. No extensions. No exceptions.** Miss this and you cannot undo it.
- **Mechanics:** File via certified mail with return receipt to the IRS service center for your state. Keep proof of mailing. Also provide a copy to the company and attach one to your tax return for the year of issuance.
- **Who should care:** Any founder receiving restricted stock subject to vesting. Common at formation. Also relevant for early employees receiving restricted stock (though most employees get options, which have different tax treatment).

This is not optional to think about. Route to `early-legal-checker` for complete treatment and to an attorney or CPA for execution.

---

## Common Scenarios

### Solo bootstrapped founder, W-2 day job, SaaS side project

- **LLC in home state** is usually right. Keeps compliance light, shields personal assets, simple tax filing.
- If revenue grows past ~$80k in a year and day job ends, consider S-Corp election.
- If fundraising becomes plausible, plan to convert to Delaware C-Corp at that point.
- **IP assignment risk from the day job is the dominant concern** — run `early-legal-checker` before forming anything.

### Two co-founders, no current plans to fundraise

- **Multi-member LLC** is often right. Flexible membership interests, pass-through taxation, simpler than C-Corp.
- Operating agreement must be drafted carefully — this is where most co-founder disputes originate.
- If fundraising becomes plausible, conversion to C-Corp will cost $5k–$15k and some negotiation with any existing members.

### Two or more co-founders, planning to raise a seed round

- **Delaware C-Corp from day one** is almost always right. Pay the $500 for Stripe Atlas or Clerky, issue restricted stock with vesting to all founders, file 83(b) within 30 days, and move on.
- Doing this right at formation is cheap; fixing it later is expensive.

### Regulated industry (healthcare, legal, accounting, licensed professions)

- Many states require a Professional Corporation (PC) or Professional LLC (PLLC) with ownership restricted to licensed practitioners.
- Do not choose an entity until you have talked to a lawyer licensed in your state and domain.

### Non-US founder forming a US business

- Most common path: Delaware C-Corp via Stripe Atlas. Simple, well-documented, supports remote formation.
- ITIN (Individual Taxpayer Identification Number) required for the founder to be a shareholder.
- Tax treaty considerations vary by country.
- **Consult counsel in both the US and home jurisdiction.** Treating a US C-Corp naively can trigger unexpected tax liability in the home country (controlled foreign corporation rules, etc.).

---

## Ongoing Obligations by Structure

| Obligation | LLC (plain) | LLC + S-Corp | Delaware C-Corp |
|---|---|---|---|
| State franchise tax / annual report | Varies ($0–$800/yr) | Varies + payroll filings | $300+ annual (authorized shares method can be much higher) |
| Federal tax return | Schedule C or Form 1065 | Form 1120-S | Form 1120 |
| Payroll | Only if employees hired | Required (owner must be on payroll) | Required if employees (founders often are) |
| Corporate minutes / formalities | Light (operating agreement only) | Moderate | Heavy (annual meeting, board resolutions for material decisions) |
| Foreign qualification (if operating in other states) | Yes, each state | Yes, each state | Yes, each state |
| Estimated tax payments | Owner level (quarterly) | Owner + entity level | Entity level (quarterly) |

---

## When to Pay for a Lawyer

Always, before filing, for any of these:

- Multi-member anything (operating agreement or shareholders' agreement)
- Any co-founder with unequal contributions, IP contributions from a prior role, or unusual equity terms
- Regulated industry
- Non-US founder
- Any structure being chosen to achieve a specific tax outcome (S-Corp election timing, QSBS planning, multi-state operations)
- Any scenario where founder equity exceeds ~$50k in expected value (the cost of good legal advice is a tiny fraction of the downside of getting this wrong)

For a simple single-member LLC in a low-cost state with no co-founders and no fundraising plans, self-service via LegalZoom or direct state filing is often fine. Everything else benefits from a lawyer.
