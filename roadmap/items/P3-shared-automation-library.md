# P3 — Shared automation library (SAMPLE)

- **Status:** Next · ◐ validating
- **Outcome:** every automation is built once and reused by the next team — the rebuild tax disappears, and each new use case starts further down the field.
- **Team:** platform (me)
- **Unlocks:** E2 (copilot enablement), E5 (team-built agents) — reuse is what lets enablement scale past what one builder can ship.
- **Measure:** reusable components in the library (target: grow the current 9); reuse rate — automations pulled from the library vs. built new.

## Log

- 2026-06-28 — created from the pattern emerging across P1/P2 builds: the same connectors and prompt scaffolds keep getting rewritten. Scope: a curated, versioned library, not a dumping ground.
- 2026-07-06 — first champion automations from E2 wave 1 landing here. Validating the intake bar — a component only counts as "reusable" once a second team adopts it unchanged.
