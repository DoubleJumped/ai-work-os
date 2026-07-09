# Prompt: Friday rollup

<!-- Runs Fridays ~3pm as a Cowork scheduled task or Claude Code routine pointed at this repo.
     This prompt file is code: when a draft comes out wrong, fix the prompt, not the draft. -->

Read CLAUDE.md and follow its rules. Then draft this week's status update:

**Inputs**
1. All `worklog/` files from the last 7 days.
2. Any file in `reference/`, `roadmap/items/`, or `intake/` modified in the last 7 days.
3. (Work instance only) my calendar and sent mail for the week via the M365 connector — read live, to catch meetings and commitments the worklog missed. Never copy their content into the repo; summarize in your own words.

**Output** — write `rollups/status-YYYY-Www.md`:

1. Group everything by item ID. For each item with a real outcome this week:
   - `### [ID] Item name — headline` (the outcome in one line, not the activity)
   - 1–2 sentences of what happened, linking the underlying files
   - `**Why it matters:**` the so-what for a reader who doesn't track details
   - `**Next step:**` what happens next; name anything needed from the reader
2. Items that moved without a headline outcome: one line each under `### Also moved`.
3. `### Intake movement` — new U#s, score changes, graduations.
4. `### Learned this week` — new/updated reference files worth knowing, one line each.
5. `### Flags` — blockers and decisions needed, stated plainly. If none, omit the section.
6. Worklog lines with no tag: park verbatim under `### Unfiled` for me to sort.

**Rules**
- Outcomes, not activity. "Cut E3's cost assumption in half" — never "did pricing research."
- Plain language for a manager-then-director audience; gloss any model or tool name on first use.
- Numbers only if a file backs them; label target vs measured.
- Do not editorialize on my behalf on anything in Flags — state the fact and the ask, I'll set the tone.
- Append a `(agent)` line to today's worklog noting the rollup was drafted.
- (Work instance) also export the finished draft as a .docx to the boss-facing OneDrive folder and update the SharePoint status page.

This is a draft — I edit before anything leaves the repo.
