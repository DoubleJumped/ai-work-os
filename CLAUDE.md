# Agent contract for this repo

This folder is a personal work OS: worklogs, a research reference library, a living roadmap, and generated rollups. You (the agent) are expected to read and write here across many sessions. These rules are the contract; follow them exactly.

## Before answering anything factual

1. Check `reference/INDEX.md` first. If a relevant file exists, read it and answer from it.
2. Every volatile fact in `reference/` carries `(as of YYYY-MM-DD, source: <url>)`. If the stamp is older than the file's staleness window (declared in its frontmatter; default 30 days for pricing/limits/versions, none for stable definitions), re-verify against the source, update the fact and the stamp in place, and note the change in today's worklog.
3. Only web-search when the reference library has no answer or the stamp is expired. After any web search worth keeping, file the result (rules below).

## Filing research

- One topic per file in `reference/`. If a file covers two topics or exceeds ~150 lines, split it and update the index.
- Distill — file the answer, not pasted search results. Facts get `(as of date, source: url)` stamps.
- Supersede, don't append: when a fact changes, overwrite the old value in place and bump the stamp. Never leave two files or lines asserting different values for the same fact — git history preserves the old value.
- Before creating a new file, check the index for an existing file with a similar title or the same source URL; update it instead of duplicating.
- Frontmatter on every reference file: `topic`, `volatility` (`stable` | `check-quarterly` | `check-monthly`), `related` (item IDs and other reference files).
- After writing or updating a file, update its one-line entry in `reference/INDEX.md` — in the same action, never "later." An index that lies is worse than no index.
- If a new fact changes an assumption on a roadmap or intake item (cost, feasibility, timing), add a dated line to that item's `## Log` in `roadmap/items/` or `intake/`, tagged with the reference file. This is the link that makes research show up in rollups.

## IDs and linking

- `P#` = platform capability, `E#` = enablement engagement, `U#` = intake candidate. The registry of live IDs is `roadmap/roadmap.md` and `intake/queue.md`.
- Tag worklog lines, log entries, and rollup items with `[ID]` in square brackets. Multi-item lines get multiple tags.
- Never re-use a retired ID. Retired items move to `roadmap/items/archive/` with status `retired` or `done`; their IDs stay reserved.

## Writing to the worklog

- You may append to today's worklog (`worklog/YYYY-MM-DD.md`, create from `worklog/_template.md` if missing) to record work you performed: research filed, stamps refreshed, rollups drafted. Prefix agent-written lines with `(agent)`.
- Never rewrite or delete existing worklog lines. Worklogs are append-only.

## Generating rollups

- The Friday rollup prompt is `prompts/friday-rollup.md`; follow it verbatim. Output goes to `rollups/status-YYYY-Www.md`. Group by item ID; format each item as headline → why it matters → next step. Outcomes, not activity.
- Drafts are drafts: the human edits before anything leaves this repo.

## Hygiene you own

- When you touch a file, fix what you find: dead links, entries missing from the index, missing stamps. Note fixes in the worklog with `(agent)`.
- Contradictions between files: the newer stamp wins; correct the older file and note it. If genuinely unclear, flag it in the worklog instead of guessing.

## Hard rules

- This is the HOME TEMPLATE: sample content and your own general research only. Never put real employer data, names of colleagues, or work-confidential material in this copy.
- (Work instance) never copy other people's chats, emails, or shared documents into this repo — query them live via connectors instead. Only content the owner authored belongs here.
- Never delete files without being asked; archive instead (`docs/06`).
