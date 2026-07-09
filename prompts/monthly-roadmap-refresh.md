# Prompt: monthly roadmap refresh

<!-- Run on the last working day of the month, interactively (this one is a conversation, not a fire-and-forget). -->

Read CLAUDE.md. This is the monthly roadmap refresh — propose, don't apply, until I approve each change.

1. Read every file in `roadmap/items/` (skip archive/), this month's `rollups/`, and `intake/queue.md`.
2. Propose card moves and confidence changes on `roadmap/roadmap.md`, each with its evidence cited from item logs
   (e.g. "E3 ◐→●: cost assumption halved 07-09, quality bar validated 07-21").
3. Propose U→E graduations for intake items scoring ≥70, and flag any intake item now scoring above a current roadmap item.
4. Recompute scorecard numbers from the files; show your working. Anything not backed by a file stays at its old value, flagged.
5. Flag drift: items with no log entries in 30+ days — for each, ask: done, stalled, or retire?
6. After I approve: apply the changes to roadmap.md, update the ID registry, regenerate `roadmap/onepager.html`
   from the approved board, and remind me to export the PowerPoint for the upward copy.
7. Append a `(agent) [meta]` worklog line summarizing what changed.
