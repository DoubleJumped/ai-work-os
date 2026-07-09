# P1 — Document intelligence core (SAMPLE)

- **Status:** Now · ● in production
- **Outcome:** any team's documents become a searchable, auditable knowledge source — built once, pointed at each new corpus in days, not months.
- **Team:** platform (me)
- **Unlocks:** E1, E3, E4 — every document-heavy use case in the intake queue rides on this.
- **Measure:** time-to-onboard a new corpus (target: < 1 week); retrieval accuracy on each team's eval set.

## Log

- 2026-06-10 — created. v1 shipped for internal testing: ingestion, chunking, retrieval, citations.
- 2026-07-02 — decision: retrieval evals are per-corpus, not global — each team signs off on THEIR eval set before go-live. This is the audit story that makes governance reviews fast.
