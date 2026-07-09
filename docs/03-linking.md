# 03 — Linking: how one fact travels the whole system

**The backbone is a single convention: item IDs in square brackets. This doc traces one real-shaped example end to end so the mechanics are unambiguous.**

## The ID registry

| Prefix | Meaning | Lives in | Example |
|---|---|---|---|
| `P#` | Platform capability — built once, reused by every engagement | `roadmap/items/P*.md` | P1 Document intelligence core |
| `E#` | Enablement engagement — a team served, an outcome delivered | `roadmap/items/E*.md` | E3 Regulatory & compliance drafting |
| `U#` | Intake candidate — scored, queued, not yet on the roadmap | `intake/queue.md` | U4 French-language support |

IDs are assigned once, never re-used. `roadmap/roadmap.md` and `intake/queue.md` are the registry. When U4 graduates to the roadmap it becomes the next free E# (the queue entry records `→ became E6`).

## The worked example: Luna → E3

**Tuesday, 2:05 pm.** You price out the 5.6 model family. Luna turns out to cost roughly half what the E3 cost estimate assumed. Here is every write that happens, in order:

**1. The fact lands in the library** — `reference/model-pricing.md`:

```markdown
## 5.6 family (SAMPLE DATA — placeholder numbers)
- Luna:  $0.80 / MTok in, $4 / MTok out  (as of 2026-07-09, source: vendor pricing page)
- Terra: $1.60 / MTok in, $8 / MTok out  (as of 2026-07-09, source: vendor pricing page)
- Sol:   $4.00 / MTok in, $20 / MTok out (as of 2026-07-09, source: vendor pricing page)
Implication: Luna meets the E3 drafting quality bar at ~½ the cost assumed in the E3 estimate.
```

**2. The assumption changes on the item** — `roadmap/items/E3-regulatory-drafting.md`, under `## Log`:

```markdown
- 2026-07-09 — [ref] Luna pricing halves the per-document cost assumption
  (see ../../reference/model-pricing.md). Cost estimate revised; strengthens
  the case to move E3 up. Flag for monthly roadmap refresh.
```

**3. The worklog gets its one line** — `worklog/2026-07-09.md`:

```markdown
- 14:05 [E3][ref] Priced 5.6 family — Luna ≈ half our cost assumption for compliance
        drafting. Filed reference/model-pricing.md, updated E3 log
```

Three writes, ~3 minutes (or zero — an agent doing the pricing research performs all three under CLAUDE.md rules).

**4. Friday, unattended.** The rollup job collects the week's worklog lines, groups by ID, follows the links for context, and drafts in `rollups/status-2026-W28.md`:

```markdown
### [E3] Regulatory & compliance drafting — cost assumption cut in half
Priced the 5.6 model family this week: Luna meets our drafting quality bar at ~½ the
per-document cost in the current E3 estimate (details: reference/model-pricing.md).
**Why it matters:** E3's business case just got materially stronger.
**Next step:** revalidate the quality bar on real filings; propose moving E3 up at the
monthly roadmap refresh.
```

Your boss reads that Monday morning — headline, why, next step, with a link to the underlying file. Not "researched model pricing."

**5. End of month.** The roadmap refresh (docs/05) reads the E3 log, and the card moves or its confidence changes — with a paper trail from the director-visible card all the way down to a Tuesday-afternoon worklog line. **Nothing was reconstructed from memory at any step.**

## Link direction rules (what points where)

- **Worklog → everything** via `[ID]` tags and file mentions. The worklog is the chronological spine; it links out, nothing links into it.
- **Reference → items** via `related:` frontmatter and "Implication" lines. Reference files never contain status — they contain facts. Status lives on items.
- **Items → reference** via log-entry links. An item's log is its memory: every assumption change cites the file that caused it.
- **Rollups → all of the above**, generated. Never hand-edit facts into a rollup — fix the source file and regenerate, or the correction exists nowhere durable.

## Why not a database / task tracker / wiki?

Plain files with a naming convention are what both Claude (file-native) and you (any editor, any machine, greppable, git-diffable) handle best, with zero schema to outgrow. The discipline lives in CLAUDE.md instead of a schema — which means an agent can hold it for you. If the org later wants Planner/ADO views, they can be *generated* from these files; the reverse migration is never as easy.
