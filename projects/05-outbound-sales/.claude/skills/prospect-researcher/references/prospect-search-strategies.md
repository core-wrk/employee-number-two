# Prospect Search Strategies

This is an internal reference for the `prospect-researcher` skill. It is a playbook of 5 sourcing strategies for finding outbound prospects via publicly accessible web search, with the query patterns, credibility considerations, and third-party amplifiers for each. **Do not show this document to the founder.** Use it to pick the right strategy based on the founder's starting input, then walk them through it in plain language.

---

## Strategy Selection Matrix

| Founder's starting input | Primary strategy |
|---|---|
| "I have a list of target companies" | Strategy 1: Targeted company team page mining |
| "I know the role I'm looking for, not the companies" | Strategy 2: Job title search on LinkedIn |
| "I want to find who's using [Competitor]" | Strategy 3: Competitor customer mining |
| "I want to find companies showing buying signals right now" | Strategy 4: Trigger event search |
| "I've seen my buyer hanging out in [community]" | Strategy 5: Community member mining |
| "I have no idea where to start" | Start with Strategy 2 using the ICP's named role |

You can combine strategies — Strategy 3 + Strategy 4 is particularly powerful (find companies evaluating a competitor AND showing a buying trigger).

---

## Strategy 1: Targeted Company Team Page Mining

**When to use:** The founder has a list of target companies (5–50) and needs to find the right named person at each one.

**Approach:**
1. For each company, search for `site:[company-domain] /team` or `site:[company-domain] /about` to find the public team page.
2. If the team page is not public, search `site:linkedin.com/in "[role]" "[company]"` to find LinkedIn profiles of people in the target role at that company.
3. Cross-reference against the company's website to confirm the role is current (LinkedIn profiles go stale).
4. Capture the profile URL as the source.

**Credibility considerations:**
- LinkedIn profiles are the primary source of truth for role and company, but 10–20% are out of date. When in doubt, check the person's last post or activity date — stale profiles often have no recent activity.
- Company team pages are more current but often only list senior leadership, missing the actual buyer roles.

**Third-party amplifiers (surface inline when relevant):**
- **LinkedIn Sales Navigator** — makes this strategy 5x faster with filters by title, company, and recent activity. $99/mo personal tier is worth it for founders who are doing outbound seriously.
- **Apollo.io** — has role-filtered company search and includes verified emails. Free tier covers ~50 lookups per day.
- **Clay** — enrichment-first, pay-per-lookup, integrates with ~50 data sources.

---

## Strategy 2: Job Title Search on LinkedIn

**When to use:** The founder knows the buyer role but does not have specific target companies yet.

**Approach:**
1. Use LinkedIn search via web: search `"[role]" "[industry]"` (e.g., `"VP Sales Enablement" "B2B SaaS"`) and filter to the target geography.
2. LinkedIn profiles are public and indexed by Google — query pattern: `site:linkedin.com/in "[role]" "[size indicator]"` (e.g., `site:linkedin.com/in "VP Sales Enablement" "SaaS"`).
3. For each profile found, capture the URL, confirm the company from the profile headline, and cross-reference the company against the ICP's size range (check the company's LinkedIn page for employee count).
4. Tier A/B/C/D using the rubric.

**Credibility considerations:**
- Public LinkedIn search is reliable for title and company; less reliable for email. Emails are not publicly exposed through search.
- Some results will be from larger enterprise companies that fall outside a mid-market ICP — filter aggressively at Step 3.
- LinkedIn's own search UI behind login gives better filtering but requires the founder to be logged in; the plain web search works fine for cold sourcing.

**Third-party amplifiers:**
- **LinkedIn Sales Navigator** — the native tool, with the best filters. Notably worth it if this is the primary strategy.
- **Apollo.io** — role-filtered search with contact data attached.
- **ZoomInfo** — enterprise-tier, highest accuracy and coverage, expensive.

---

## Strategy 3: Competitor Customer Mining

**When to use:** The founder knows a specific competitor's customers are high-fit for their product — usually because the product competes on positioning or offers a differentiated feature.

**Approach:**
1. Find G2 reviews of the competitor: `site:g2.com "[competitor name]" reviews`. Each G2 review is written by a real customer and typically names the reviewer's role and company.
2. Alternative: look at the competitor's case study page — public case studies name the customer company and often the featured individual.
3. Alternative: search `"[competitor name]" "using" site:linkedin.com` to find LinkedIn posts from customers discussing the competitor.
4. For each customer company surfaced, use Strategy 1 to find the right named person (the G2 reviewer's exact name may not be useful — the actual buyer may be a different person).

**Credibility considerations:**
- G2 reviews are semi-public and LinkedIn-authenticated, which makes them high-signal sources.
- Case study customers may have been given financial incentives — still valid prospects, but note in the row that they are a featured case study.
- Never quote the review content in outreach without attribution — it is public but still owned by the reviewer.

**Third-party amplifiers:**
- **G2 Buyer Intent** — paid tier that tells you which companies are actively researching categories you compete in. Expensive but precise.
- **6sense / Bombora** — enterprise intent data platforms. Overkill at this stage.
- **Crossbeam** — partner-enabled, useful only if the founder already has CRM data to share.

---

## Strategy 4: Trigger Event Search

**When to use:** The founder wants to find prospects showing active buying signals — not just "who could buy" but "who is shopping right now."

**Approach:** Search for public signals of trigger events:

1. **Recent hiring:** `site:linkedin.com "we're hiring" "[role]" "[ICP role]"` — finds LinkedIn posts from companies announcing new hires in the buyer's adjacent roles. Example: `site:linkedin.com "we're hiring" "SDR" "VP Sales Enablement"` finds posts where the VP of Enablement is announcing SDR hires (meaning they are scaling the team and will care about onboarding speed).
2. **Recent funding:** Search Crunchbase or TechCrunch for recent Series A/B/C raises in the ICP's vertical. Funded companies have budget and are expanding teams.
3. **Public complaints:** Search Reddit and LinkedIn for public complaints about the problem the founder is solving — people complaining about onboarding time, ramp time, tool stack, etc. These people are sometimes themselves the buyer.
4. **Conference activity:** Search for speakers and attendees at conferences in the ICP's space. Speakers are often visible buyers and are easier to outreach to because they are performing publicly.
5. **Job postings:** The company's own job postings often reveal their tool stack, pain points, and priorities. Search `site:boards.greenhouse.io "[industry]"` or `site:jobs.lever.co "[role]"` for postings that mention specific problems.

**Credibility considerations:**
- Trigger events are high signal, but they are also often caught by every other prospector in the world. Move fast or find triggers that are less obvious.
- LinkedIn hiring posts decay fast — a post from 3 months ago is stale; a post from last week is fresh.
- Funding announcements are often followed by 200 cold emails in the first week after the announcement. Stand out by waiting 2–3 weeks so the founder is not drowned out.

**Third-party amplifiers:**
- **Crunchbase** — funding data, free tier works for this stage
- **The Org / Built In** — team growth and new hire signals
- **LeadIQ / SignalHire** — intent-signal aggregators

---

## Strategy 5: Community Member Mining

**When to use:** The ICP's "Where to Find Them" section names specific communities (Slack groups, Discord servers, subreddits, Pavilion, Revenue Collective, SaaStr, etc.) and the buyer is visible in those communities.

**Approach:**
1. For each named community, surface the publicly visible members (leaders, frequent posters, people who have asked questions relevant to the problem space).
2. On Reddit: `site:reddit.com/r/[subreddit] "[problem keyword]"` to find people who have posted about the problem.
3. On Slack/Discord communities that have public member lists: look for the role-based channels or the introductions channels.
4. On Pavilion, Revenue Collective, SaaStr: speaker lists from events are often publicly indexed.
5. Capture the person, their community, and what they posted/said (this becomes personalization fuel for `email-drafter`).

**Credibility considerations:**
- Community mining has a high personalization ceiling — reaching out referencing a specific post someone made is materially different from cold outreach.
- Community norms matter: never use a community as a prospect list in a way that violates the community's rules. Reddit specifically penalizes cold outreach that references Reddit posts; LinkedIn is more tolerant.
- Ask the founder whether they are already a member of the community — reaching out as a fellow member is materially different from reaching out as an outsider.

**Third-party amplifiers:**
- **Gummy Search** — search across Reddit more efficiently than Reddit's native search
- **CommonRoom** — aggregates community activity across Slack, Discord, Reddit, LinkedIn
- **Pavilion / Revenue Collective membership** — if the founder joins the community, access to the member directory makes this strategy dramatically easier

---

## General Principles Across All Strategies

1. **Always capture the source URL.** Every prospect row must have a citation — the LinkedIn profile URL, the team page URL, the G2 review URL. No citation, no row.
2. **Never invent data.** If you cannot find the prospect's role, company size, or email, mark it `[unknown]` and add the enrichment note.
3. **Always cross-reference the ICP.** A prospect that looks good via Strategy 2 still needs to pass the ICP tiering rubric. Sourcing is upstream of qualification.
4. **Start with one strategy per run.** Do not try to run all 5 strategies in a single session — pick the one that fits the founder's starting input and go deep. Iterate in future sessions.
5. **Surface third-party tools inline, never block on them.** The skill works entirely without any paid tool. Tools 10x the speed; they are not requirements.
6. **Move fast on fresh signals.** Strategy 4 trigger events have a short half-life. A funding announcement from 6 months ago is not a trigger event; it is a historical note.
