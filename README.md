# AI Work OS

A file-based operating system for an AI Specialist role: capture what you do daily, file what you learn permanently, link everything to a living roadmap, and let agents draft the reporting. Everything is plain markdown so both you and AI agents can read, write, and reason over it.

**This copy is the home template.** The worklogs, roadmap, and rollups are sample content showing the system in use; `reference/` holds only the file template here — the real research corpus this template incubated was split out to [ai-platform-research](https://github.com/DoubleJumped/ai-platform-research) (2026-07-14) so the reusable system and the living research can evolve separately. The work instance lives in OneDrive/SharePoint at work and never touches personal GitHub — see [docs/07-work-setup.md](docs/07-work-setup.md).

## The loop

```
capture (daily, 2 min)          worklog/2026-07-09.md
   │
file (as research happens)      reference/model-pricing.md   ← stamped, sourced
   │
link (one convention: IDs)      [E3] tags connect worklog ↔ reference ↔ roadmap
   │
rollup (Friday, automated)      rollups/status-2026-W28.md   ← agent-drafted, human-edited
   │
roadmap (monthly refresh)       roadmap/roadmap.md + one-pager for the boss
   │
review (quarterly)              narrative pre-read + scorecard to director level
```

Nothing is ever reconstructed from memory. The Friday status, the monthly roadmap, the quarterly review, and your year-end brag document are all *derived* from the same files by agents, on schedule.

## Repo map

| Path | What lives there | Written by |
|---|---|---|
| `CLAUDE.md` | The agent contract — rules every AI session follows here | you (curated by hand) |
| `docs/` | The manual — numbered guides, read in order | you |
| `worklog/` | One file per day; decisions, deltas, unblocks | you (+ dictation) |
| `reference/` | The knowledge library — one topic per file, indexed, date-stamped | you + agents |
| `roadmap/` | The board (`roadmap.md`), one file per item (`items/`), the shareable one-pager | you + agents |
| `intake/` | Scored use-case queue (value × feasibility) | you |
| `rollups/` | Friday statuses + quarterly reviews, agent-drafted | agents (you edit) |
| `prompts/` | The exact prompts for every scheduled/recurring job | you (curated) |
| `decks/` | Slide decks derived from the research (self-contained HTML) | agents (you edit) |

## Quick start

1. Read `docs/01` through `docs/08` in order (≈45 min total).
2. Replace the sample roadmap items in `roadmap/items/` with your real ones. IDs are the backbone — assign them first.
3. Start the daily note habit today: copy `worklog/_template.md` to `worklog/YYYY-MM-DD.md`.
4. Set up the Friday rollup job (`docs/04`) within the first week — the payoff that makes the habit stick.
5. Monthly: refresh the roadmap (`docs/05`). Quarterly: run the review (`prompts/quarterly-review.md`).

## The one convention that holds it together

Every roadmap item has an ID: **P#** (platform capability), **E#** (enablement engagement), **U#** (intake candidate, pre-roadmap). Every worklog line, reference note, rollup entry, and roadmap card that relates to an item carries its ID in square brackets: `[E3]`. That single convention is what lets an agent trace "Luna is half the cost we assumed" from a Tuesday worklog line to the Friday status to the roadmap card your director sees. The full worked example is in [docs/03-linking.md](docs/03-linking.md).

## What agents do here

Any Claude session pointed at this folder reads `CLAUDE.md` and follows its rules: check `reference/INDEX.md` before web-searching, refresh facts past their staleness window, file new research with stamps and sources, and tag everything with item IDs. The repo *is* the agent's long-term memory — sessions come and go, the files accumulate. How that stays healthy as it grows is [docs/06-memory-and-growth.md](docs/06-memory-and-growth.md).
