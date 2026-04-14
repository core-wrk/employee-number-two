# Acceptance Criteria — Patterns

Internal reference for `epic-requirements-builder`. Acceptance criteria are the contract with the implementer. A criterion that cannot be checked pass/fail without interpretation is a criterion that will be disputed at QA time.

---

## Canonical Form

> **AC-NN:** Given [precondition], when [action], then [observable outcome].

The Given/When/Then structure is not mandatory, but every AC must contain its three parts in some form.

---

## Testable vs. Non-Testable

**Non-testable (do not ship):**
- "The export is fast."
- "The UI is intuitive."
- "Errors are handled gracefully."
- "The page loads quickly."

**Testable (ship):**
- "Given a dataset of 10,000 rows, when the user clicks Export, then a CSV download link is delivered by email within 30 seconds."
- "Given a form with a required email field, when the user submits without filling it, then the field is highlighted in red and the screen reader announces 'Email is required'."
- "Given a network failure during submission, when the user retries, then the submission succeeds without creating a duplicate record."
- "Given a cold page load, when measured on a throttled Fast 3G connection, then first-contentful-paint occurs within 1.5 seconds."

---

## Patterns by Scenario Type

### Happy path

> **AC-01:** Given [normal setup], when [user performs primary action], then [expected success outcome is visible/persisted/delivered].

### Error path

> **AC-02:** Given [condition that should fail], when [user attempts the action], then [specific error is shown and the system state is unchanged].

### Edge / boundary

> **AC-03:** Given [extreme but valid input — max length, max size, boundary value], when [action], then [system handles it per specification].

### Permissions

> **AC-04:** Given [user without permission], when [they attempt the action], then [403 or permission-denied UI shown and no data is accessed].

### Concurrency

> **AC-05:** Given [two users acting on the same resource], when [both submit within the same window], then [last-write-wins / optimistic-lock-error / merged state — specify which].

### Performance (with a number)

> **AC-06:** Given [load condition], when [measured], then [metric is under threshold].

### Observability

> **AC-07:** Given [action executed], when [log/metric inspected], then [the named event is emitted with the expected fields].

---

## Agent-Mode ACs

In agent mode, prefer ACs that can be expressed as automated tests. A coding agent can self-check tests; it cannot easily self-check a vague criterion.

**Good for agent mode:**
- "Running `npm test -- export` passes all assertions."
- "Running `curl -X POST /api/exports` with valid auth returns a 202 with a job ID."
- "Running the lint and typecheck commands exits zero."

**Also acceptable:** criteria that the agent can verify by reading the code it wrote, as long as the verification is unambiguous.

---

## Human-Mode ACs

In human mode, criteria can include manual verification steps. A human QA reviewer can do things a coding agent cannot (use a screen reader, evaluate subjective UX, test on a real device).

**Good for human mode:**
- "QA reviewer can open the exported CSV in Excel without warnings."
- "QA reviewer can navigate the full flow using only a keyboard."
- "QA reviewer confirms the error message uses the brand voice."

---

## Common Failure Patterns

### Compound ACs

> Bad: **AC-01:** The export works, is fast, and is accessible.

Three ACs. Split.

### ACs that restate FRs

If the AC is identical to the FR just rewritten, it is not adding value. ACs should specify the *conditions of acceptance* — preconditions, observable outcomes — that make the FR checkable.

### Missing precondition

> Bad: **AC-01:** When the user clicks Export, a file is downloaded.

Precondition matters: signed in or not? How much data? What plan tier? Without the Given, the criterion is ambiguous.

### Unverifiable outcomes

> Bad: **AC-01:** When the user clicks Submit, the request is processed correctly.

"Correctly" is the word that kills acceptance criteria. Name the observable outcome: status code, UI change, data persisted, email sent.

---

## Number of ACs Per FR

A typical FR generates 2–4 ACs: one happy path, one error path, one edge case, occasionally one permissions check. If a single FR is generating 8+ ACs, the FR is probably too broad and should be split.

---

## AC Numbering

Number ACs across the entire epic (AC-01, AC-02, AC-03...), not within each FR. This makes them easier to cite in QA reports and keeps the requirements doc readable as a flat list.
