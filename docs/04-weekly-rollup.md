# 04 — The Friday rollup

**Every Friday afternoon, an agent drafts your weekly status from the files; you edit for five minutes; your boss reads it Monday morning with clickable links. The human does judgment, the machine does assembly.**

## Inputs the job reads

1. **This week's worklogs** — `worklog/` files from the last 7 days. The primary source.
2. **Files modified this week** — anything in `reference/`, `roadmap/items/`, `intake/` with a last-modified date in the window. Catches research and assumption changes even if a worklog tag was missed.
3. **(Work instance) calendar + sent mail via the M365 connector** — to catch meetings and commitments that never made it into a note. Read live from the Graph; never copied into the repo.

## Output format

`rollups/status-YYYY-Www.md` — grouped by item ID, each item exactly:

```markdown
### [ID] Item name — headline (the outcome, in one line)
One or two sentences of what happened, with links to underlying files.
**Why it matters:** the "so what" for someone who doesn't track the details.
**Next step:** what happens next and what, if anything, is needed from the reader.
```

Plus three short sections: **Intake movement** (new U#s, score changes), **Learned this week** (new/updated reference files worth knowing about), and **Flags** (blockers, decisions needed — the only place a request for help appears, stated plainly).

Format rules the prompt enforces (`prompts/friday-rollup.md`):

- **Outcomes, not activity.** "Cut E3's cost assumption in half" — not "did pricing research." If a week's work on an item produced no outcome worth a headline, it gets one line under a catch-all "Also moved," not a padded section.
- **Plain language.** The reader is a manager, then a director. No model names without a gloss, no acronyms that aren't already house vocabulary.
- **Links on headlines** so a curious reader can drill down — to the SharePoint copies in the work instance (docs/07).

## Setting up the job

**Option A — Claude Cowork scheduled task (recommended first).** Create a scheduled task, weekly, Friday ~3 pm, with the prompt from `prompts/friday-rollup.md`. Constraint that shapes everything: **Cowork's *scheduled* runs execute in the cloud and cannot see local-only folders** — the repo must be in OneDrive/SharePoint (work) or a cloud location Cowork can reach. This is why the work instance lives in OneDrive from day one.

**Option B — Claude Code routine.** Cloud-side scheduled run with the same prompt; supports cron expressions if you want a different cadence. Equivalent result; use whichever surface you'll actually check.

**Option C — Copilot Scheduled Prompt (parallel, not instead).** Microsoft's native weekly-summary prompt ("review my inbox, calendar and Teams activity from the past seven days...") scheduled for Friday. It can't see the repo (Copilot doesn't index markdown — docs/07) but it sees the Graph exhaustively. Early on, run A **and** C and diff them: whatever Copilot catches that your rollup missed is a capture gap to fix. Retire C when it stops finding anything.

## The human pass (Friday, 5 minutes)

The draft is a draft. Before it goes anywhere:

1. **Check emphasis** — the agent ranks by activity volume; you re-rank by what actually matters upward.
2. **Check the Flags section hardest** — asks and blockers are the highest-stakes lines and the ones an agent is most likely to state too softly or too strongly.
3. **Cut** — anything that doesn't change what the reader knows or does. Shorter reads as more in control.
4. Ship it: in the work instance the job also emits the **boss-facing mirror** — a .docx or an updated SharePoint page (one stable URL your boss bookmarks). Markdown stays canonical; the mirror is for Copilot-visibility and one-click reading (docs/07).

## Failure modes

- **Empty worklog week** → the job falls back to file-modification dates and (work) the Graph, and flags the capture gap. Two flagged weeks in a row = the habit needs attention; fix the habit, don't fake the log.
- **Untagged lines** → parked under "Unfiled" in the draft for you to tag or discard. A recurring "Unfiled" pile means tags need to be easier — shorten the ID list, not the discipline.
- **The draft reads like a diary** → the prompt's outcome-framing rules need tightening; fix `prompts/friday-rollup.md`, don't hand-fix every week. The prompt file is code — improve it once, benefit every week after.
