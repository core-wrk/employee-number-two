# Dependency Validation Rules

Internal reference used by `epic-definer` in Phase 7. Epic dependencies are the edge list of a directed acyclic graph; violations corrupt the backlog and propagate confusion into `roadmap-builder` and Project 07.

## What "Dependency" Means

Epic B depends on Epic A if at least one of these is true:

1. **Hard dependency:** B cannot ship because it technically requires A's output (e.g., B uses a database table that A introduces).
2. **Value dependency:** B can ship but cannot produce its expected value without A (e.g., B is a report built on a dataset that only A populates).
3. **Sequencing dependency:** B should not ship before A for strategic reasons (e.g., B is a premium feature that only makes sense after A's free-tier foundation).

Capture all three kinds in the Dependencies column. Distinguish them in the epic's Notes if the distinction matters.

## Validation Checks

Run these in Phase 7 before writing the file.

### Check 1: No Cycles

A directed acyclic graph has no cycles. Example violation:

- E02 depends on E05
- E05 depends on E09
- E09 depends on E02

**How to detect:** Walk the dependency graph. Standard DFS cycle detection. If any cycle is found, surface it to the founder:

> "Found a dependency cycle: E02 → E05 → E09 → E02. One of these dependencies is wrong. Walk me through it — which one isn't actually a dependency?"

**How to resolve:** Usually one of the edges is mislabeled — it's a strategic preference, not an actual dependency. Break that edge. Document in Notes.

### Check 2: No Priority Contradictions

An epic cannot have higher priority than its dependencies. Example violation:

- E02 is P0
- E02 depends on E07
- E07 is P3

**How to detect:** For each epic, check that every dependency has priority ≥ the dependent's priority.

**How to resolve:** Either:
1. Bump the dependency's priority (E07 from P3 → P0), or
2. Demote the dependent (E02 from P0 → P3), or
3. Challenge the dependency — is E07 really required for E02?

Ask the founder:

> "E02 is P0 but depends on E07 which is P3. Either E07 needs to be P0, or E02 can't actually be shipped in the next cycle, or the dependency is wrong. Which is it?"

### Check 3: No Dangling References

Every ID in a Dependencies column must reference an epic that exists in the backlog. Example violation:

- E05 depends on E99
- E99 does not exist

**How to detect:** Iterate every Dependencies cell, parse IDs, verify each exists.

**How to resolve:** Either:
1. Create the missing epic (if the dependency is real), or
2. Remove the reference (if it was a typo or stale), or
3. Surface the gap — "E99 isn't in the backlog. Was this meant to be a new epic? If so, let's define it now."

### Check 4: No Self-References

An epic cannot depend on itself. Example violation:

- E03 depends on E03

Trivial to detect. Usually a copy-paste error. Remove the self-reference.

### Check 5: No Dependencies on Cut Epics

If E05 depends on E02 and E02 is `Status=Cut`, that's a problem. The cut means the dependency either must be satisfied another way, or E05 needs to be re-thought.

**How to detect:** For each non-cut epic, check that every dependency has `Status != Cut`.

**How to resolve:**
1. Find a different path to satisfy the dependency (rewrite E05's scope), or
2. Cut E05 too (cascading cut), or
3. Un-cut E02 if the scope is still needed.

Surface to founder:

> "E05 depends on E02, but E02 was cut 3 weeks ago. Does E05 still make sense? If yes, the dependency needs to change."

### Check 6: Dependencies on Shipped Epics Are Fine

A dependency on a `Status=Shipped` epic is fine — the dependency is already satisfied. No action needed. But still keep the edge in the graph for historical traceability.

## Dependency Density Heuristics

After validation, look at the graph shape. Red flags:

- **Star graph with one epic having 8+ dependents.** That epic is a platform epic — should probably be P0 even if RICE is low. It's the keystone.
- **Long chains (A → B → C → D → E).** Long dependency chains are brittle. The founder will feel unable to start anywhere without finishing the first 3 epics. Look for ways to parallelize or decouple.
- **Densely coupled clusters.** If 5 epics all depend on each other pairwise, they're probably one epic in disguise. Merge.
- **Zero dependencies across the whole backlog.** Unlikely to be true. Probably the founder didn't think about dependencies. Prompt: "Walk me through E02 — is there really no other epic that needs to happen first?"

## Dependency Format in the Table

Dependencies column uses comma-separated epic IDs:

```
E01, E03
```

Or `—` for none.

**Do not use other symbols.** No arrows, no parentheses, no strikethrough for cut-cascaded dependencies — those go in Notes. The table is parsed by downstream tools; keep it clean.

## Documenting Dependency Rationale

For non-obvious dependencies (especially sequencing dependencies), capture rationale in the epic's Notes:

> **E05 Notes:** Depends on E02 as a sequencing dependency — E05 is the premium tier of the capability E02 introduces. Shipping E05 before E02's free tier is live would cannibalize the pricing strategy.

Hard dependencies usually don't need rationale (they're technically obvious). Value and sequencing dependencies often do.

## Dependency Changes in Re-Runs

When re-running `epic-definer`:

- If a dependency edge changes, surface it in the preview: "E05 previously depended on [E02, E07]; now depends on [E02]. E07 dependency removed because [reason]."
- Never silently drop a dependency. Surface every change.

## Dependencies vs. Related-Work Links

Not everything that "touches the same area" is a dependency. Examples of **not dependencies**:

- Two epics both use the ICP data table (shared resource, not dependency)
- Two epics are parts of the same pillar (co-located in PRD, not dependency)
- Two epics were discussed together in the same discovery call (shared context, not dependency)

Dependencies should change the *order* of shipping. If two epics can ship in any order, they are not dependencies — even if they're related. Capture related-work links in Notes instead.

## When the Founder Resists Dependency Mapping

Founders sometimes skip this phase because "it'll all work out." Push back once:

> "Dependency mapping is what keeps the roadmap from being fiction. If E02 and E05 both need E07 but E07 is P2, the roadmap is wrong. It's a 10-minute conversation."

If the founder still resists, capture the gap in Notes for each affected epic ("Dependencies not validated — may need revisit") and surface the risk in `roadmap-builder` when it runs.