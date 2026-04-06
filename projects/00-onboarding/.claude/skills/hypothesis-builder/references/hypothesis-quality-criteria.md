# Hypothesis Quality Criteria

This is an internal reference for the `hypothesis-builder` skill. It defines what makes a strong vs. weak hypothesis in each area and provides examples. **Do not show this document to the founder.** Use it to calibrate when to push back and when to accept an answer.

---

## Problem Statement

### Strong
- Names a specific type of person or organization
- Describes a concrete situation where the pain occurs
- Gives some sense of frequency or intensity

**Example:** "Mid-market SaaS companies with 50-200 employees struggle to onboard new sales reps because their product knowledge is scattered across Notion docs, Slack threads, and tribal knowledge. It takes 6-8 weeks before a new rep can run a demo confidently."

### Weak
- Affects "everyone" or "businesses"
- Describes a category of problems rather than a specific pain
- No indication of severity

**Example:** "Companies have trouble with knowledge management."

### When to push back
- The problem could apply to thousands of different companies in different ways
- The founder cannot describe a specific person experiencing the pain
- There is no sense of how often or how badly this hurts

---

## Proposed Solution

### Strong
- Describes what the product does in concrete terms
- Connects the solution directly to the pain described
- Has a clear mechanism — how it works, not just what it achieves

**Example:** "An AI agent that ingests a company's existing product docs, call recordings, and CRM notes, then generates interactive training modules that new reps can practice with. It simulates customer objections using real deal context."

### Weak
- Describes a category ("a platform for...") without specifics
- Disconnected from the problem statement
- Relies on buzzwords without mechanism

**Example:** "An AI-powered knowledge management platform."

### When to push back
- The solution is described in a single sentence with no mechanism
- The founder leads with technology rather than the outcome
- The solution addresses a different problem than the one stated

---

## Key Assumptions

### Strong assumptions
- Specific and testable
- The founder can describe what evidence would confirm or refute them
- They represent real risks to the business if wrong

**Examples:**
- "Sales managers will trust AI-generated training content enough to assign it to new hires"
- "Companies will share call recordings and CRM data with a third-party tool"
- "Reducing ramp time from 8 weeks to 3 weeks is valuable enough to justify $500/month per seat"

### Weak assumptions
- Too obvious to be useful ("People want to save time")
- Too vague to test ("The market is big enough")
- Actually a hope, not an assumption ("Users will love it")

### When to push back
- The founder cannot name any assumptions — surface them from the conversation: "You mentioned X. That seems to assume Y. Is that right?"
- The assumptions are all soft truisms rather than falsifiable claims
- Fewer than 3 assumptions are articulated

---

## Target Customer

### Strong
- Describes a role, not just a company type
- Includes context about how they buy and what they care about
- Distinguishes between the user and the buyer if they are different

**Example:** "VP of Sales Enablement at mid-market SaaS companies. They report to the CRO, their budget comes from the sales ops line item, and they are evaluated on time-to-productivity for new hires."

### Weak
- Just a company size or industry
- No role or decision-maker identified
- Conflates user and buyer

**Example:** "SaaS companies" or "Sales teams"

### When to push back
- No specific role is named
- The founder says "everyone in the company would use it"
- There is no sense of who writes the check

---

## Current Alternatives

### Strong
- Names specific competitors, tools, or workarounds
- Explains what each does well and where it falls short
- Acknowledges that people are solving this problem today, even imperfectly

**Example:** "Today this is handled by a combination of Lessonly for structured training, Gong for call review, and a Notion wiki that is always out of date. The problem is these are three separate tools with no connection to each other, and none of them adapt to the rep's actual deals."

### Weak
- "Nothing like this exists"
- Names competitors but does not explain the gap
- Dismisses alternatives without understanding them

### When to push back
- The founder claims there are no alternatives — there are always alternatives, even if they are manual processes, spreadsheets, or ignoring the problem
- The founder names competitors but cannot articulate the specific gap
- The competitive analysis is surface-level ("they are too expensive" or "their UI is bad")

---

## Why Now

### Strong
- Points to a specific, observable change in the last 12-24 months
- The change is external to the founder (not "because I decided to build it")
- Creates urgency or unlocks a new approach

**Examples:**
- "LLMs can now ingest unstructured content and generate interactive simulations — this was not possible 2 years ago"
- "Remote hiring has become the default, making in-person shadowing impractical for onboarding"
- "Gartner's latest report shows sales enablement budgets grew 40% YoY — companies are actively spending here"

### Weak
- No timing argument at all
- "The market is growing" without specifics
- The timing is personal ("I finally have time to build this")

### When to push back
- The founder has no answer to "why now"
- The answer is internal rather than external
- The same idea could have been built 5 years ago with no difference
