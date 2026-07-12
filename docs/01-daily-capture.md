# 01 — Daily capture

**The habit: one markdown file per day, a couple of lines whenever you switch tasks. Two minutes total. Everything else in this system is derived from these lines, so this is the only habit that has to stick.**

## Why this shape

The research is consistent on what survives contact with a real workweek:

- **Exhaustive logging dies.** Dictating everything you do, minute-by-minute trackers, structured forms — all abandoned within weeks. Friction kills capture systems.
- **What sticks is coarse, append-only, and pays off immediately** (interstitial journaling, Google-style snippets, Julia Evans' brag documents). You write a line *because dumping the thought clears your head at the task switch*, not out of discipline.
- **Capture judgment, not activity.** The unit is a decision, a delta, an unblock, a thing learned — never a keystroke log. "Wrote code" is worthless; "chose pgvector over Azure AI Search for P1 because of cost — see reference note" is gold.

## The ritual

1. First task switch of the day: copy `worklog/_template.md` to `worklog/YYYY-MM-DD.md` (or let the agent create it).
2. At each task switch or interruption, add one line: rough time, item tag, what happened.
3. That's it. No end-of-day cleanup, no formatting debt. Friday's agent does the assembly.

Voice dictation is a fine input method if typing is the friction — dictate the line, keep the unit coarse.

## Line format

```
- 09:40 [E1] Legal approved the CS policy corpus — pilot unblocked, ingestion can start Monday
- 11:15 [P2] Decided: review checks run in CI, not as a manual gate. Rationale in items/P2 log
- 14:05 [E3][ref] Priced the 5.6 family — Luna ≈ half our cost assumption for compliance drafting.
        Filed reference/model-pricing.md, updated E3 assumptions
- 16:30 [meta] Reg. Affairs lead asked about French-language support — added to intake as U4
```

Rules of thumb:

- **Tag every line** with an item ID (`[E1]`, `[P2]`), `[ref]` when research got filed, `[meta]` for the system/program itself, `[U#]` for intake. Untagged lines are fine occasionally — the Friday agent will ask or park them — but tags are what make the automation cheap.
- **Write for the Friday agent, not for posterity.** One line of context so the rollup can say *why it matters* without you re-explaining.
- **Decisions get their rationale somewhere permanent.** The worklog line records *that* you decided; the one-sentence *why* goes in the item's `## Log` (see docs/03). Future-you asking "why did we pick X?" is the most common query this system answers.

## What does NOT go in the worklog

- Other people's content — no pasted chats, emails, or meeting transcripts. The Graph keeps those; agents query them live at rollup time (docs/04). Copying governed content into personal files is the move that violates policy — see docs/07.
- Raw research dumps — those are distilled into `reference/` (docs/02); the worklog just gets the pointer line.
- Anything you'd be uncomfortable seeing quoted in a Friday status. The worklog feeds upward reporting; keep venting elsewhere.

## The payoff schedule (why the habit holds)

- **Friday:** your status update writes itself — you edit for 5 minutes instead of reconstructing a week.
- **Monthly:** roadmap refresh is a diff, not archaeology.
- **Quarterly/annually:** review evidence and the brag document are already written, dated, and linked.
- **Daily:** the line itself clears your head at the task switch. That's the immediate reward that keeps it going.
