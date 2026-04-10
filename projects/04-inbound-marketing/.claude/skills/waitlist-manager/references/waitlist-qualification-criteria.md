# Waitlist Qualification Criteria

This is an internal reference for the `waitlist-manager` skill. It is the Tier A/B/C/D rubric used to qualify every waitlist signup against the ICP, with worked examples calibrated to the example ICP (VP Sales Enablement at 100–500 person SaaS companies). **Do not show this document to the founder.** Use it to make tier judgments consistent across runs and to push back when the founder wants to over-qualify or under-qualify a signup.

---

## Why The Tiers Matter

The point of tiering is operational, not academic. Project 08 (`beta-and-user-testing`) reads this tracker expecting Tier A signups to be ready for beta invitation. If Tier A is over-inclusive, Project 08 wastes time on bad-fit recruits. If Tier A is under-inclusive, Project 08 starves for candidates and the founder ends up cold-outreaching strangers instead of warm-inviting waitlist signups.

The tiers also serve as a feedback loop for `channel-strategist`. If most Tier A signups come from one channel, that channel is working. If most signups come from a different channel but are Tier C, that channel is producing volume but not signal — and the founder may need to rethink the channel mix.

---

## The Four Tiers

### Tier A — Exact ICP Match

**Definition:** Every key ICP attribute matches. The signup is exactly the kind of person the founder is building for.

**Required matches against `icp.md`:**
- **Role:** Matches the buyer or user role explicitly named in the ICP (or a near synonym — "VP Enablement" matches "VP Sales Enablement"; "Director of RevOps" matches "Director of Revenue Operations")
- **Company size:** Within the named range (e.g., 100–500 employees if the ICP specifies that)
- **Industry/vertical:** Matches the ICP's named verticals (e.g., B2B SaaS)
- **Geography:** US-headquartered (if the ICP specifies US primary, secondary fit)
- **At least one buying trigger:** Either explicitly mentioned in their signup (e.g., "we're hiring 10 reps in Q2") or inferable from publicly available signals (recent CRO hire, recent funding round, etc.)

**Operational meaning:** Send a discovery call invite within 7 days. These are the highest-priority candidates for beta recruitment in Project 08.

**Worked example:**
> Sarah Chen, VP of Sales Enablement at NorthStar SaaS (212 employees, B2B SaaS, San Francisco). Signed up via the LinkedIn post about ramp time. Note from her signup form: "We just brought on 8 new SDRs and our existing onboarding tool isn't moving the needle."
>
> **Tier: A**
> **Why:** Role matches exactly. Company size matches (212, in range). Industry matches (B2B SaaS). Geography matches (US). Explicit buying trigger ("8 new SDRs", "existing tool isn't moving the needle").
> **Next action:** Send discovery call invite this week.

---

### Tier B — Adjacent Fit

**Definition:** Most ICP attributes match but one or two are off. The signup is interesting and worth nurturing, but not at the top of the outreach list.

**Common patterns:**
- Right role, wrong company size (Director of Sales Enablement at a 700-person company — adjacent to mid-market but technically enterprise)
- Right industry, wrong role (Sales Operations Analyst at a SaaS company — user-adjacent but not the buyer)
- Right size and industry, wrong role (Marketing Director at a 250-person SaaS company — they signed up because they care about messaging, but they are not the buyer)
- Right buyer, missing buying trigger (no immediate hiring signal, no recent funding, no obvious urgency — could be a long-term lead)

**Operational meaning:** Add to a nurture sequence. Stay engaged via content. Re-evaluate in 30–60 days for a second pass at qualification.

**Worked example:**
> Marcus Rivera, Director of Sales Operations at GrowthCo (340 employees, B2B SaaS, Austin). Signed up via the blog post on quiz metrics. No buying trigger mentioned.
>
> **Tier: B**
> **Why:** Adjacent role (RevOps Director, not VP Sales Enablement) — could be the technical buyer in a deal but not the economic buyer. Company size matches. Industry matches. No buying trigger named.
> **Next action:** Add to nurture sequence. If Marcus engages with two more touches, escalate to Tier A and send a discovery invite.

---

### Tier C — Out of ICP, Interesting

**Definition:** Wrong role or wrong company stage, but the signup is interesting in some other way. They might learn from the founder, refer the right person, or eventually become a buyer themselves in a different role.

**Common patterns:**
- Right role at a much larger or much smaller company (VP Sales Enablement at a 5,000-person enterprise — out of mid-market range, but the role is right)
- Adjacent industry (B2B services, not SaaS — partially relevant but the buying patterns are different)
- Founder at a competitor or adjacent company (curious about what the founder is building, possibly worth a conversation but not a buyer)
- Investor or analyst (not a buyer themselves but might refer customers)
- Consultant in the space (could become a referral source)

**Operational meaning:** No active outreach. Keep them in the tracker. Revisit if their context changes (e.g., they leave the larger company and join a mid-market one).

**Worked example:**
> Jamie Park, Sales Enablement Manager at MegaCorp (4,800 employees, enterprise software, Seattle). Signed up via the YouTube video.
>
> **Tier: C**
> **Why:** Role is enablement-adjacent but the seniority is below VP/Director and the company size is way out of the mid-market range. Not a buyer, but engaged with the content.
> **Next action:** No outreach. Note in the tracker that Jamie engaged with the YouTube video — useful signal that the video is reaching enterprise-adjacent audiences.

---

### Tier D — Out of ICP, Deprioritize

**Definition:** Spam, students, competitors collecting intel, accidental signups, or signups so far out of the ICP that they are not worth tracking actively.

**Common patterns:**
- Spam form fills (random characters, obviously fake names)
- Students or job seekers (signup says "looking for a job in sales enablement")
- Competitors (the founder recognizes the email domain or company name)
- Way out of role (HR Manager at a manufacturing company — no realistic path to becoming a buyer)
- Test signups from the founder's own team

**Operational meaning:** Keep in the tracker for record-keeping (so the founder does not re-process the same email later) but do not factor into outreach planning. Tier D entries should be excluded from the "Top Tier-A this week" section and from any beta recruitment lists.

**Worked example:**
> "test test", testtest@gmail.com, no company, no role. Signed up via the homepage form on April 7.
>
> **Tier: D**
> **Why:** Obviously a test or spam fill. No real signal.
> **Next action:** None. Keep in tracker for completeness.

---

## Edge Cases And How To Handle Them

### Case 1: The role matches but the title is different

The ICP says "VP Sales Enablement" but the signup is from "Head of Revenue Enablement" at a 200-person SaaS company. Same job, different title. **Tier A.** Use the role's substance, not the literal title. Note the title variation in the tracker.

### Case 2: Company size is close but not in the named range

The ICP says "100–500 employees" but the signup is from a 600-person company. **Tier B**, with a note that the company is just above the upper bound. If the company is shrinking or recently lost a layer, it might be Tier A — ask the founder if they want to flag.

### Case 3: The signup has minimal information

A signup form only captured an email address. No name, no company, no role. The email is at a recognizable B2B SaaS company. **Default to Tier B with a note** ("missing role context, follow up to confirm fit"). If the founder cannot enrich the signup within a few days, downgrade to Tier C.

### Case 4: The signup is a personal email (gmail, outlook, etc.)

A signup with a personal email and no company. **Tier C** by default — without a company affiliation, cannot validate the most important ICP attributes. If the founder later learns the company, re-tier.

### Case 5: The signup is an obvious referral from a known Tier A

A signup form has a "How did you hear about us?" answer like "Sarah Chen at NorthStar told me." **Tier A by association.** Refer back to Sarah's profile in the tracker for context.

### Case 6: The signup is from an existing contact

The founder already knows this person — they were a colleague, a prior customer, or a friend. **Tier the signup based on their current role and company,** not on the personal relationship. Note the relationship in the notes column. Personal relationships make outreach easier but do not change the ICP fit.

### Case 7: The signup is from a competitor

A signup from someone clearly working at a named competitor in `competitive-landscape.md`. **Tier D.** Note explicitly that this is a competitor and the founder should be careful about what they share in any follow-up.

### Case 8: The signup describes themselves as a "founder" or "CEO"

If the founder is at a SaaS company in the mid-market range, their VP Sales Enablement is the actual buyer — but the founder/CEO might be the economic buyer or the champion. **Tier B** by default, with a note. If the founder/CEO is at a tiny early-stage company (under 50 employees), **Tier C** — too early for the product.

---

## How To Push Back On The Founder's Tier Judgments

The founder will often want to over-qualify Tier A. They are excited about every signup. Push back when:

- The role is wrong but the founder wants to rationalize it ("but they're influential at their company")
- The company is too big or too small ("they might use it for a small team")
- The signup has no buying trigger ("but they're a great fit")

The founder will sometimes also want to under-qualify Tier A. Push back when:

- They are skeptical of their own outreach ("they probably don't really care")
- They are afraid to ask for a discovery call ("it's too soon to reach out")

The rubric exists to be the tie-breaker. Apply it consistently.
