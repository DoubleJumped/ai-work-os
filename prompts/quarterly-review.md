# Prompt: quarterly review pre-read

<!-- Run ~1 week before the quarterly review. Output is a short written narrative — the research
     is unambiguous that a 1-2 page memo sent 48h ahead beats a slide deck. -->

Read CLAUDE.md. Draft the quarterly review pre-read from this quarter's evidence:

**Inputs:** the quarter's `rollups/`, all item logs in `roadmap/items/` (including anything archived this quarter), `intake/queue.md`, and the current `roadmap/roadmap.md` scorecard.

**Output** — `rollups/review-YYYY-Qn.md`, 1–2 pages, four sections:

1. **What shipped** — each completed/advanced item as outcome + measured result. Measured numbers only; targets labeled as targets.
2. **What we learned** — 3–5 honest lessons, including what didn't work. A review with no misses reads as spin.
3. **Where the roadmap moves** — the Now/Next/Later changes this quarter and why, in prose. Attach the one-pager; don't duplicate it.
4. **Decisions needed** — explicit, numbered, each with a recommendation. This is the only section that asks for anything, and everything it asks for is specific and small.

**Rules:** written narrative, full sentences — no bullets-as-thinking. A director should read it in five minutes and know exactly what happened, what it cost, what it returned, and what you need. Scorecard (Readiness / System health / Value) as a closing table.
