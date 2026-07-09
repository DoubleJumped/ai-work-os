# P2 — Governed agent harness (SAMPLE)

- **Status:** Now · ● committed
- **Outcome:** every AI build starts from curated templates with security standards and automated review checks — compliant by default, so governance review is a formality, not a fight.
- **Team:** platform (me)
- **Unlocks:** E1 and every build after it; this is what makes enabling *other* teams safe.
- **Measure:** % of builds passing governance review first-time (target: 100%); time from idea to approved build.

## Log

- 2026-06-18 — created. Modeled on Alberta's "well-built harness" (docs/08-sources.md): hand-curated templates, never AI-generated — the harness is the one thing the AI doesn't write.
- 2026-07-09 — decided: review checks run in CI, not as a manual gate. Human review moves to the template layer (curate once) instead of the per-build layer (bottleneck forever).
