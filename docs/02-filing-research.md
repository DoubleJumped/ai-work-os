# 02 — Filing research

**The rule: research is filed the moment it happens, as part of the same session — never "organized later." Later never comes.**

The `reference/` folder is the knowledge library: what you (and your agents) have already figured out, so nobody figures it out twice. Over a year this becomes the asset that separates "Graeme googles fast" from "Graeme's system already knows."

## The filing flow, step by step

Say today you looked up the 5.6 model family — Sol, Terra, Luna — and their pricing.

1. **Distill.** The deliverable is the answer, not the search: what each model is, what it costs, what it's good for. Three facts, not thirty tabs.
2. **Decide stable vs volatile.** *What Luna is* — stable, write once. *What Luna costs* — volatile, will drift. This distinction drives everything else.
3. **File to the right place.** Stable definitions → `reference/model-families.md`. Pricing → `reference/model-pricing.md`. One topic per file. New topic → new file from `reference/_template.md`.
4. **Stamp every volatile fact:** `(as of 2026-07-09, source: <url>)`. The stamp is what stops an agent from confidently quoting January's pricing in June — and the source URL is what makes re-verification a 30-second job instead of a fresh research session.
5. **Update `reference/INDEX.md`** — one line per file. The index is how agents find the right file in one read instead of scanning the folder.
6. **Link it forward.** If the fact changes an assumption on a roadmap or intake item — Luna's price halves the cost estimate for E3 — add a dated line to that item's `## Log`. This step is what makes research surface in Friday's rollup (full trace in docs/03).
7. **Tag the worklog:** `[E3][ref] Priced 5.6 family — Luna ≈ half assumed cost. Filed reference/model-pricing.md`.

Steps 3–7 take under five minutes by hand. **When an agent did the research, they take zero minutes** — end the session with "file this per the repo rules" and CLAUDE.md handles the rest. Over time, agents do most of the filing; you do the curating.

## Reading it back (the other half of the loop)

The payoff pattern, enforced by CLAUDE.md:

- An agent asked "what does Luna cost?" checks `reference/INDEX.md` → reads `model-pricing.md` → answers from the file. No web search.
- If the stamp is past the file's staleness window, the agent re-verifies against the source URL, updates the fact and stamp *in place*, and notes the refresh in the worklog. Lookups keep the library fresh instead of just consuming it.
- If the library has no answer, the agent researches — and files the result. **Every miss becomes a future hit.** That's the compounding.

## Quality bar for reference files

- **Short.** A screenful or two. Past ~150 lines, split it (docs/06).
- **Answer-shaped.** Someone (human or agent) with a question should get the answer in ten seconds. Lead with the facts; background goes last or nowhere.
- **Sourced.** Every non-obvious claim carries its URL. Unsourced facts are rumors.
- **Honest about placeholders.** Sample content in this template is marked as such — an agent must never mistake illustrative numbers for real ones.

## What belongs in reference/ — and what doesn't

| Belongs | Doesn't — goes instead to |
|---|---|
| Model definitions, pricing, limits | — |
| Vendor/tool capabilities and gotchas | — |
| How-tos you'll need twice (auth setup, export pipelines) | — |
| Decisions and their rationale | the item's `## Log` in `roadmap/items/` |
| Meeting outcomes, who-said-what | worklog line (yours) or the Graph (others') |
| Anything scraped from colleagues' content | nowhere in this repo — query it live (docs/07) |
