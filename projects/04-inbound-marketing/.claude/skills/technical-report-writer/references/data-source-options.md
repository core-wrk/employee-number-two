# Data Source Options

This is an internal reference for the `technical-report-writer` skill. It describes the four credible data sources for industry research reports, with cost tiers, credibility notes, and how to recommend each. **Do not show this document to the founder.** Use it to walk the founder through their options when they do not yet have data.

---

## When To Use This Reference

Use this when the founder wants to write a research report but does not yet have real data. The skill must refuse to draft a hollow report — instead, redirect the founder to gather data first. This reference is the conversation guide for that redirection.

The four credible sources, in approximate order from cheapest to most expensive:

1. Scraped public data
2. Original survey
3. Expert interviews
4. Third-party purchased data

---

## Source 1: Scraped Public Data

**Cost:** Time. The financial cost is near-zero.

**Time to gather:** 1–4 weeks for a meaningful corpus, depending on the source.

**What it is:** Data from publicly accessible sources that the founder aggregates, cleans, and analyzes — often in a way nobody else has done before. Examples:

- **SEC filings** — Public companies file 10-Ks, 10-Qs, and S-1s. Searchable via EDGAR. Useful for financial benchmarks, headcount data, segment breakdowns.
- **Job postings** — Aggregated job posting data (LinkedIn, Indeed, company career pages) reveals hiring patterns, in-demand skills, organizational structure changes. Tools like Revealera or Lightcast can help; manual scraping is also possible.
- **GitHub repos** — Public commit data, repo activity, language distribution. Useful for developer-tool reports.
- **Reddit / Hacker News threads** — Sentiment, recurring complaints, vendor mentions. Useful for category awareness and pain validation.
- **Public reviews** — G2, Capterra, TrustRadius reviews are public and aggregable.
- **Census / BLS data** — US Census, Bureau of Labor Statistics, OECD. Useful for macro trends in employment, industry size, geography.
- **Government datasets** — data.gov, regulators (CFPB for finance, FDA for healthcare), state-level open data portals.
- **Conference attendance / speaker lists** — public on event websites, useful for industry network analysis.

**Strengths:**
- Free
- Defensible (every data point traces to a public source)
- Often a fresh angle nobody else has aggregated

**Weaknesses:**
- Selection bias from what is public (private companies and roles are missing)
- Time-intensive to collect and clean
- May require some technical skill (scraping, data cleaning)

**Best for:** Founders with technical comfort, narrow research questions where public data covers the audience, and time to invest in data work.

**Example:** "We analyzed 3,400 job postings for Sales Enablement roles posted between January and December 2025. 78% mentioned 'AI coaching' as a desired skill — up from 12% in 2023. Most of those postings still listed 'content authoring' as a primary job duty, suggesting that AI coaching is being added on top of existing enablement roles rather than replacing them."

---

## Source 2: Original Survey

**Cost:** $0–$2,000 depending on tool and incentives.

**Time to gather:** 2–6 weeks (1 week to design, 2–4 weeks to field, 1 week to analyze).

**What it is:** The founder designs a survey targeting people in the ICP, distributes it through their network and channels, and analyzes the responses.

**Tools:**
- **Free tier:** Google Forms, Tally, Typeform free tier. Adequate for short surveys with basic logic.
- **Paid:** Typeform paid, SurveyMonkey, Qualtrics. Better for longer surveys, branching logic, and incentives.

**Distribution:**
- Founder's existing network (LinkedIn, email list, community memberships)
- Communities the founder is part of (Pavilion, RevGenius, Sales Assembly, niche Slack/Discord)
- Paid distribution (Pollfish, Centiment, Prolific) — more expensive, less targeted
- Partner with a community or association (cheapest way to reach a curated audience)

**Incentives:** Whether to offer one is a tradeoff. Cash incentives ($10–$50 gift cards) increase response rates but skew responses toward people who want the incentive. Charitable donations are often a better fit for B2B audiences.

**Sample size guidance:**
- Floor: 50 responses for any meaningful claim
- Comfortable: 100+ responses
- Strong: 200+ responses

**Strengths:**
- Direct from the ICP
- Quotable (verbatim responses are the strongest evidence in research reports)
- Establishes the founder as the source of original data on a question

**Weaknesses:**
- Selection bias (people who fill out surveys are not a random sample)
- Self-report bias (people answer aspirationally, not honestly)
- Time-intensive distribution

**Best for:** Founders with a network they can credibly reach, narrow research questions where 50–200 responses gives statistical power, and willingness to do community-based distribution.

**Example:** "Survey of 142 VP-level Sales Enablement leaders at US-based SaaS companies (100–500 employees), February 2026. Recruited via Pavilion community and direct LinkedIn outreach. Median tenure in role: 2.4 years."

---

## Source 3: Expert Interviews

**Cost:** Time. Financial cost: $0 (unless the founder pays for interviewees, which is rare in B2B).

**Time to gather:** 4–8 weeks for 10–20 interviews.

**What it is:** The founder schedules 30–60 minute interviews with people in the ICP, asks structured questions, and synthesizes patterns across the conversations.

**Recruitment:**
- The founder's existing network
- Cold outreach via LinkedIn (15–25% response rate is normal for well-targeted outreach)
- Warm intros from advisors, customers, and investors

**Format:**
- Recorded with consent (so the founder can quote verbatim with permission)
- Semi-structured: 8–12 questions, with room for follow-up
- 30–60 minutes per interview

**Sample size:**
- Floor: 10 interviews for any pattern claim
- Comfortable: 15–20 interviews
- Saturation typically hits at 12–15 for a well-targeted population (after this, new interviews stop adding new patterns)

**Strengths:**
- The strongest verbatim quotes any report can have
- Direct relationship with people who become candidates for design partner conversations
- Patterns surface that would not show up in surveys (because interview follow-up reveals nuance)

**Weaknesses:**
- Slow (each interview takes 60–90 minutes including scheduling and notes)
- Not statistically generalizable
- Selection bias from who agrees to be interviewed

**Best for:** Founders who like talking to people, founders who want the interview process to double as design partner discovery, and reports where rich qualitative findings matter more than statistical claims.

**Example:** "Based on 18 interviews with Sales Enablement leaders at mid-market SaaS companies, conducted January–March 2026. Interviewees had between 1.5 and 6 years of tenure in role. All interviews recorded with permission; quotes anonymized at interviewee request."

---

## Source 4: Third-Party Purchased Data

**Cost:** $500–$10,000+ depending on the source and the data scope.

**Time to gather:** 1–4 weeks (most data providers can deliver within days; analysis takes longer).

**What it is:** The founder buys access to a dataset from a third-party provider and synthesizes or reframes the data for their report.

**Providers:**
- **Crunchbase Pro** — funding, headcount, growth signals. ~$50–500/month.
- **Statista** — pre-aggregated industry stats. Per-report or subscription pricing.
- **PitchBook** — private market data. Enterprise pricing, usually only accessible via partnership or trial.
- **CB Insights** — startup and tech industry research. Enterprise pricing.
- **Lightcast / Burning Glass** — labor market and skills data.
- **Industry associations** — many trade associations sell or license their member data.

**Strengths:**
- Saves the time of original collection
- Credibility of an established provider
- Often includes data the founder cannot collect themselves (e.g., private company financials)

**Weaknesses:**
- Cost
- Less differentiated (other companies have access to the same data)
- Licensing restrictions (some providers do not allow data resharing or charts in published reports without a separate license)
- Stale data (subscription data is sometimes months out of date)

**Best for:** Founders with budget, founders writing about markets where private company data matters, and founders who need a credibility-by-association boost from a known provider.

**Important:** Always check the licensing terms before publishing. Some providers prohibit including their charts in published research without a separate license. Always cite the provider explicitly.

---

## How To Recommend

When the founder asks "what data should I use?", the answer depends on three factors:

| Founder situation | Recommended source |
|---|---|
| Has a network in the ICP, comfortable with outreach | Original survey OR expert interviews |
| Has technical comfort, narrow research question, public data exists | Scraped public data |
| Has budget, needs credibility-by-association | Third-party purchased data |
| Has none of the above | Start with expert interviews — lowest financial cost, builds the network |

The cheapest path is usually expert interviews. The most defensible path is usually scraped public data. The fastest path is usually third-party purchased data. The richest qualitative findings come from interviews. The strongest statistical claims come from surveys.

A real research report often combines two sources — for example, scraped public data for the macro context plus expert interviews for the qualitative texture. Combining sources strengthens the report and makes it harder to dismiss.

---

## When To Tell The Founder To Wait

If the founder cannot commit to gathering one of these four sources within 4–8 weeks, do not draft a research report. Tell them the report is premature. Suggest:

1. Run `blog-writer` for a position post on the same topic in the meantime — that does not require data
2. Run `linkedin-writer` for a series of posts that test whether the topic resonates with the audience
3. Come back to `technical-report-writer` once they have either committed to a data-gathering plan or actually have data

A research report published without data is worse than no report. It damages the founder's credibility for years.
