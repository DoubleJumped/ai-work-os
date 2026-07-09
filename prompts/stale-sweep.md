# Prompt: consolidation sweep (quarterly — Oct / Jan / Apr / Jul)

<!-- The maintenance job from docs/06. Report first; nothing is archived or deleted without approval. -->

Read CLAUDE.md and docs/06-memory-and-growth.md. Run the consolidation sweep and give me a report before changing anything:

1. **Stale facts** — every `(as of ...)` stamp past its file's volatility window. For each: re-verify from the source URL and bump the stamp, or recommend archiving if the topic is dead.
2. **Index integrity** — files in `reference/` missing from INDEX.md (orphans) and index entries with no file (danglers).
3. **Duplicates** — two files sharing a source URL or near-identical titles; propose merges.
4. **Contradictions** — files disagreeing on the same fact; newer stamp wins, propose the correction to the older.
5. **Dead items** — roadmap items with no log entries in 60+ days; for each ask: done, stalled, or retire?
6. **Size thresholds** — reference files over ~150 lines (propose splits); INDEX.md over ~200 lines (propose per-domain sub-indexes); CLAUDE.md over ~200 lines (propose what moves to docs/).
7. **Contract audit** — read CLAUDE.md top to bottom against how the repo is actually being used this quarter; flag rules that are contradicted, ignored, or missing.

Then: apply what I approve, archive with the standard banner (never delete without asking), and append a `(agent) [meta]` worklog line summarizing the sweep.
