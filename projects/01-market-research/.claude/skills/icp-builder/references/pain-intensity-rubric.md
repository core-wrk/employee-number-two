# Pain Intensity Rubric

This is an internal reference for the `icp-builder` skill. It defines how to rate the severity of the customer's pain on a 1–5 scale based on research evidence. **Do not show this document to the founder.** Use it to anchor the pain intensity rating in the ICP document and to push back when the founder wants to claim a 5/5 without supporting evidence.

---

## The 1–5 Scale

### 5/5 — Hair on fire
The customer actively complains, urgently shops for solutions, and will switch or buy on a short timeline because the status quo is actively hurting them right now.

**Required evidence (all):**
- Multiple public complaints in the last 6 months using urgent language ("killing us," "desperate for a fix," "costing us $X")
- Evidence of active shopping: "looking for alternatives to X," comparison threads, requests for recommendations
- Quantifiable cost of inaction (lost revenue, churn, compliance risk, regulatory penalty)
- At least one example of someone paying for a bad solution out of desperation

**Rare rating.** Most B2B problems do not rate 5/5. If the founder insists on 5/5, check all four evidence criteria against the research. If any are missing, rate 4 and explain why.

---

### 4/5 — Painful and acknowledged
The customer describes the problem clearly, has tried workarounds, and would evaluate a solution if it came across their desk — but is not actively shopping.

**Required evidence (at least 3 of 4):**
- Public complaints in the last 12 months with specific examples
- Evidence of a current workaround (spreadsheet, manual process, point tool) with complaints about the workaround
- Customers have tried existing solutions and been dissatisfied
- The problem is a named KPI, OKR, or metric that someone is measured on

**This is the most common high-value rating.** Most successful products serve a 4/5 problem for their initial customers. 4/5 is a real problem with a real market — it does not require hair on fire.

---

### 3/5 — Annoyance with workarounds
The customer recognizes the problem as a problem, but has a workaround that "works well enough." Would use a better solution if it were cheap and easy to adopt, but will not go looking for one.

**Indicators:**
- Complaints exist but are framed as "annoying" or "inefficient" rather than "painful"
- The workaround is tolerated for years without active complaint
- The budget to solve this is not pre-allocated — a purchase would have to be justified
- The decision would default to the cheapest option

**Products serving 3/5 problems** tend to have long sales cycles, high churn, and difficulty commanding premium pricing. They can succeed but need a different business model (PLG, usage-based, very low price point) than products serving 4/5 or 5/5.

---

### 2/5 — Latent / unrecognized
The customer has the problem but does not label it as a problem. They have adapted to it and accept it as normal. A solution would have to educate them about the problem before it could sell.

**Indicators:**
- The problem is not discussed publicly in forums or reviews
- Customers describe the situation as "just how it is"
- No existing tools or workarounds — because no one has framed it as worth solving
- The founder's hypothesis about the pain is coming from the founder's insight, not from customer signal

**Products serving 2/5 problems** can be category-creating — but they are expensive to sell because every sale requires teaching the buyer about the problem first. This is a valid strategic choice but should be a conscious one, not a default.

---

### 1/5 — No real pain
The problem the founder thinks exists does not actually exist for the customer, or the customer does not experience it the way the founder expects.

**Indicators:**
- Research surfaces no evidence of the problem from customers
- When customers are asked about the problem, they are indifferent or confused
- The founder's belief in the pain is based on their own experience or theory, not customer research

**If the research comes back 1/5, surface it honestly.** The founder probably does not want to hear it, but the cost of building a product nobody wants is much higher than the cost of hearing this in Project 01. The `hypothesis-refiner` skill will help them decide what to do next.

---

## How to Apply the Rubric

1. **Read the research outputs.** Identify every instance where the research touched on pain.
2. **Classify each instance.** Does this quote/finding support a 5, 4, 3, 2, or 1?
3. **Count by bucket.** How many 5s? How many 4s? Etc.
4. **Assign the rating.** The rating should be the highest level at which you have multiple independent pieces of supporting evidence. A single 5/5 quote does not make the overall pain a 5/5 — it is an outlier. Three or more 5/5 quotes across different sources starts to make a 5/5 case.
5. **Write the justification.** The one-sentence justification in `icp.md` should name the strongest evidence. Example: "Rated 4/5 because three separate G2 reviews of Lessonly in the last 6 months describe the problem as a measurable cost to productivity, and a Reddit thread with 47 upvotes in r/salestech named 'ramp time' as the #1 frustration."

---

## Common Mistakes

- **Rating high because the founder feels the pain strongly.** The founder's own experience of the pain is not evidence of how strongly the customer experiences it.
- **Conflating 'many people have this problem' with 'the problem is painful.'** Breadth and intensity are different. A mild problem can affect millions; a severe problem can affect thousands.
- **Rating low because the founder feels attacked.** Delivering a 2/5 or 3/5 rating is uncomfortable, but softening it helps no one. The refined hypothesis can account for it.
- **Averaging across segments.** If the pain is 5/5 for a small segment and 2/5 for a broader segment, do not rate 3/5 and call it a day. Narrow the ICP to the segment where the pain is 5/5, and note the broader segment as an expansion opportunity for later.
