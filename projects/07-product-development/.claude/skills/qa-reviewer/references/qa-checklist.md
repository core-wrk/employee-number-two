# QA Checklist

Internal reference for `qa-reviewer`. For every epic QA pass, walk through these categories. Not every item applies to every epic — skip items that are not relevant, but be able to justify the skip.

---

## Functional correctness

- [ ] Every FR in the requirements has an evaluation
- [ ] Every AC has been explicitly checked, not batch-approved
- [ ] The happy path has been verified (there is evidence in the implementation input)
- [ ] At least one error path has been verified
- [ ] Edge cases from the EC list have each been considered

## Data integrity

- [ ] Any data written by the new code is shaped correctly (matches expected schema)
- [ ] Database migrations, if any, are reversible or have a documented rollback path
- [ ] No data loss is possible from the happy path
- [ ] Deletes cascade (or do not cascade) per explicit requirement
- [ ] Constraints (unique, not-null, foreign key) are enforced where the requirements imply

## Security

- [ ] Authorization checks are present where the FR implies a permissions boundary
- [ ] User-supplied input is validated and sanitized where appropriate
- [ ] Secrets (API keys, tokens) are not hardcoded or committed
- [ ] New endpoints require auth unless explicitly public
- [ ] Error messages do not leak sensitive information (user existence, internal paths, stack traces)

## Performance

- [ ] Any NFR with a performance target has been addressed in the implementation (caching, indexing, async job, etc.)
- [ ] No obvious N+1 query patterns introduced
- [ ] Heavy operations are async/backgrounded if the NFR implies they should be
- [ ] Rate limits or throttling are in place where specified

## Observability

- [ ] Events specified in the NFR Observability section are actually emitted
- [ ] Errors are surfaced to the error-tracking provider (Sentry or equivalent)
- [ ] Log statements include enough context to debug from logs alone (user ID, resource ID, operation)

## Reliability

- [ ] Retry logic is present where the NFR specifies it
- [ ] Idempotency is enforced where the NFR specifies it
- [ ] Timeouts are set on external calls
- [ ] Failure modes have explicit handling, not silent swallowing

## Testing

- [ ] Tests exist for the happy path of each major FR
- [ ] Tests exist for at least one error path
- [ ] Tests are not disabled, skipped, or marked xfail
- [ ] Tests pass locally per the evidence provided

## Documentation and handoff

- [ ] Any new environment variables are documented
- [ ] Any new external dependencies (npm packages, Python libraries) are justified
- [ ] Any feature flag states are documented
- [ ] Any manual migration steps are documented

## UI and UX (if applicable — but UX depth is `ux-design-reviewer`'s scope)

- [ ] Empty states exist where data could be absent
- [ ] Loading states exist where operations are not instant
- [ ] Error states are visible to the user (not silent)
- [ ] Success states confirm the action worked
- [ ] Forms indicate which fields are required before submission
