# 06 — Agent memory and growth: keeping this healthy at 500 files

**This repo is the agents' long-term memory: sessions are ephemeral, files accumulate. Left alone, knowledge bases rot — studies find 20–40% of unmaintained KBs are stale or irrelevant within a year. This doc is the maintenance regime that prevents that, built from Anthropic's memory-tool guidance, community memory-bank patterns, and temporal-validity research.**

## The mental model: three memory tiers

Borrowed from MemGPT/Letta's architecture, mapped to plain files:

| Tier | Role | Here | Discipline |
|---|---|---|---|
| **Core** | always loaded, every session | `CLAUDE.md` + the indexes | keep tiny — under ~200 lines each |
| **Recall** | recent history, searched often | `worklog/`, current items | append-only, date-named |
| **Archival** | cold storage, read on demand | `reference/`, `archive/` | indexed, stamped, superseded in place |

The core tier is the expensive one: CLAUDE.md loads *in full* every session, and adherence measurably drops as it grows — **keep it under 200 lines, forever.** When a rule set outgrows it, split into topic files and reference them; the contract stays lean, the detail loads on demand.

## The five rules that prevent rot

**1. The index is atomic with the files.** Never create, rename, or archive a reference file without updating `INDEX.md` in the same action — an index that lies is worse than no index, because agents trust it. Orphaned files (exist, not indexed) are invisible; dangling entries (indexed, don't exist) burn a read. The monthly refresh includes an orphan check (`prompts/stale-sweep.md`); if drift keeps happening, enforce it with a hook rather than discipline.

**2. Supersede, don't append.** When a fact changes — Luna's price moves — **overwrite the old value in place and bump the stamp.** Never leave two files (or two lines) asserting different values for the same fact: temporal-validity research shows contradictory stale/current pairs are the single worst failure, because a stale fact *looks* just as retrievable as a current one. One topic per file makes supersession clean. History isn't lost — git keeps every prior value.

**3. Stamps are a gate, not decoration.** Every volatile fact carries `(as of date, source: url)` and every reference file declares its `volatility`. The contract rule: **a fact past its window is treated as unverified — re-verify before citing as current.** Windows: `check-monthly` for pricing/limits/versions, `check-quarterly` for vendor capabilities and org facts, `stable` for definitions. When re-verification confirms the value, bump the stamp anyway — the stamp records *last verified*, not *last changed*.

**4. Archive with a banner; git-delete the merely wrong.** Three destinations, by kind:
- **`archive/`** (in `roadmap/items/` and `reference/`) for *outdated but historically meaningful* — shipped engagements, superseded-but-instructive research. First line of every archived file: `> ARCHIVED YYYY-MM-DD — not authoritative. Superseded by: <file or "nothing">`. The banner is what an agent sees first, so archived content can't be cited as current.
- **Git history** for *simply wrong now* — delete from the tree; the content survives in history at zero context cost, and grep stops finding it.
- **Hard delete** for noise and true duplicates.

**5. Close the loop.** Every time an agent had to web-search because the library lacked the answer, the finding gets written back as a stamped fact + index line — that's already the CLAUDE.md contract. The inverse matters too: **a knowledge base is only as healthy as its usage loop.** If you notice you're web-searching things this repo should know, that's not a personal failing to push through — it's a filing gap to fix that day.

## Growth thresholds (when to restructure)

- **A reference file passes ~150 lines** → split by subtopic, update the index. Files an agent reads whole should stay comfortably under a screen-or-three.
- **`reference/INDEX.md` passes ~200 lines** → split into per-domain sub-indexes (`reference/models/INDEX.md`, `reference/m365/INDEX.md`) with the top index pointing at them. **The index size, not the file count, is the real scaling limit.**
- **Folders stay shallow — two levels, three at most.** Every pattern that scaled uses flat-ish folders + strong index + good filenames; deep taxonomies die because nothing agrees on where things go. Filenames do heavy lifting: `model-pricing.md`, `2026-07-09.md` — an agent locates by name without opening anything.
- **Retrieval infrastructure: you will not need it.** Grep + index + targeted reads is what the serious coding agents themselves use, and it comfortably handles hundreds of files — the industry threshold where anything fancier pays off is thousands of documents, and even then the 2026 answer is a better index, not a vector database. If someone proposes embeddings for this repo, the correct response is a better `INDEX.md`.

## The quarterly consolidation sweep

Aligned with the Oct/Jan/Apr/Jul checkpoints. Run `prompts/stale-sweep.md`; the agent reports, you approve:

1. **Stale facts** — stamps past their window → re-verify or archive.
2. **Orphans and danglers** — index/folder mismatches → fix.
3. **Duplicates** — same source URL or near-same title in two files → merge.
4. **Contradictions** — two files disagreeing on one fact → newer stamp wins, older corrected.
5. **Dead items** — roadmap items with no log entries in 60+ days → done, stalled, or retired; decide, don't drift.
6. **CLAUDE.md audit** — re-read the contract top to bottom: rules that no longer match how you actually work get fixed *in the contract*, because agents follow what's written, not what you meant. Contradictory instructions make agents pick arbitrarily.

Everything between sweeps is **event-driven, not scheduled**: facts update when the event that changed them happens (that's what stamps and the filing habit are for). The sweep only catches what the events missed — if sweeps keep finding lots of rot, the daily loop is broken; fix that, don't sweep harder.

## How it should feel over time

- **Month 1:** the library misses more than it hits; most answers still come from the web (and get filed). Normal.
- **Month 3:** common questions answer from files; the Friday rollup runs on rails; the roadmap refresh takes 30 minutes.
- **Month 6:** agents refresh stale pricing without being asked; the reference library answers a colleague's question before they finish asking; you hand a team a copy of this structure as their starter (the rule of three, applied to the system itself).
- **Month 12:** the annual review writes itself from 50 rollups; the archive of shipped E-items *is* the program's track record; and the repo demonstrably knows things no single session — and no single person's memory — could hold. That's the compounding you were asking for.
