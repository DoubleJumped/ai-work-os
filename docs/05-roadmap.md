# 05 — The roadmap: maintaining it and presenting it upward

**Two artifacts, one source of truth: `roadmap/roadmap.md` (canonical, markdown, yours) and the one-pager (`roadmap/onepager.html` → PowerPoint export, your boss's). The board refreshes monthly; the format never surprises anyone.**

## Format: Now / Next / Later, two bands

The research verdict was decisive, so this is fixed unless leadership asks otherwise:

- **Now / Next / Later columns, not a dated Gantt.** Dates outside "Now" create false precision and turn strategy reviews into slippage interrogations. Now = committed and dated; Next = validated, discovery underway, 1–2 quarters; Later = direction, no dates. Confidence markers: ● committed / ◐ validating / ○ direction.
- **Two swimlane bands.** Top: **Enablement** (E# — teams served, wins delivered). Bottom: **Platform** (P# — capabilities underneath). Every E-card lists `built on: P#`; every P-card lists `unlocks: E#`. This linkage is the single most important framing device in the whole system: **platform work is never shown as standalone tech — it's always the thing underneath a named business win.** That's what keeps foundational work funded.
- **A strategy strip on top** (problem / 90-day proof point / one metric that matters / the ask) and a **three-pillar scorecard** below (Readiness / System Health / Value) — capability built, not just dollars saved.

## The monthly refresh (30–45 min, agent-assisted)

Run `prompts/monthly-roadmap-refresh.md`. The agent:

1. Reads every `roadmap/items/*.md` log for the month plus the month's rollups.
2. Proposes card moves and confidence changes, **each citing its evidence** ("E3 ◐→●: cost assumption halved 07-09, quality bar validated 07-21").
3. Updates scorecard numbers from the files (use cases live, library components, verified hours/week).
4. Flags drift: items with no log entries in 30+ days (stalled or done — decide which), intake candidates scoring above roadmap items (queue jumping the plan — decide deliberately).

You accept/reject each proposal, then regenerate the one-pager and export the PowerPoint.

## The upward path (this is cultural, not technical)

- **You maintain:** `roadmap.md` + `onepager.html`. Fast to edit with an agent, git-diffable, always current.
- **Your boss gets: a PowerPoint one-pager, monthly.** Directors open, forward, annotate, and present .pptx — they do not bookmark web apps. Generate it from the HTML (PptxGenJS script or WebToSlides) or keep a slide master and update it by hand; either way the deck is *derived*, never the source.
- **The living link:** host the one-pager on a SharePoint page (work instance) so "where are we on AI?" always has one stable URL between monthly decks.
- **Quarterly:** a short written narrative (1–2 pages: what shipped, what we learned, what we're asking for) sent 48h before the review, with the one-pager attached. Decisions requested explicitly under a "Decisions needed" heading — never implied. `prompts/quarterly-review.md` drafts it from three months of rollups.

## Item files (`roadmap/items/`)

One file per ID, from `_template.md`: outcome statement, status + confidence, `built on` / `unlocks`, team, and the `## Log` — the item's append-only memory. The log is where rationale lives ("why did we descope X?") and what the monthly refresh reads. When an item ships or retires, set its status, add a closing log entry (outcome achieved, measured result), and move the file to `items/archive/`. Archived E-items are your case studies; their measured results feed the scorecard and every future pitch.

## Writing rules for anything director-visible

- Every item is phrased as its outcome: "agents answer policy questions in seconds" — not "deploy RAG pipeline."
- Numbers only when verified; "target" vs "measured" always labeled. One inflated hours-saved claim costs more credibility than ten modest real ones buy.
- The ask is always explicit and small: access, a champion, 30 minutes. Roadmaps that never ask for anything read as hobbies; roadmaps that ask for too much read as empires. Small concrete asks read as a program.
