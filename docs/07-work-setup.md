# 07 — Porting this to work (the org instance)

**The home repo is the template; the work instance is a OneDrive/SharePoint folder in the org's M365 tenant. Work content never touches personal GitHub; the template never contains work content. Improvements to the *system* (prompts, docs, conventions) flow home→work as files; facts never flow work→home.**

## One-time setup checklist

1. **Create the folder in OneDrive** (work account): copy this repo's structure minus `.git`. OneDrive placement is load-bearing, not convenience — Cowork's *scheduled* jobs run in the cloud and cannot reach local-only folders, and SharePoint/OneDrive is what makes every file linkable in rollups.
2. **Transfer the template once.** The repo is public — zip download from GitHub in any browser, no login needed.
3. **Ask IT about the Microsoft 365 connector for Claude** — Anthropic's sanctioned MCP integration (read-only, delegated permissions, honors existing access controls, audit-logged). It needs Entra tenant-wide admin consent, so this is an official request, not a personal setting. As AI Specialist you're the natural sponsor — and shepherding it through review is itself a P-item (it unblocks every future Claude use case org-wide, yours included).
4. **Set up the Friday job** (docs/04) and a **Copilot Scheduled Prompt** in parallel for the first month.
5. **Create the boss-facing surface:** a SharePoint page (or shared folder) where the rollup mirror and the roadmap one-pager live at stable URLs. Send your boss exactly one link, once.

## The Copilot / Claude split (the architectural fact that shapes everything)

| | Microsoft Copilot | Claude (Cowork / Code) |
|---|---|---|
| Reasons over | the Graph: mail, calendar, Teams, indexed docs | files: this repo, plus the Graph via the M365 connector |
| Sees the repo? | **No — Copilot does not index .md files**, even in OneDrive | Yes — natively |
| Sees your mail/chat? | Yes, natively | Yes, via connector (read-only) |
| Role in this system | catch-what-capture-missed; org-side summaries; the tool you *enable others* with | runs the system: filing, rollups, refreshes, drafting |

Two consequences:

- **The .docx mirror.** Anything Copilot should be able to see (your boss asking Copilot "what's Graeme's team shipping?") needs a Word/PDF copy in OneDrive. The Friday job emits it automatically. Markdown stays canonical; mirrors are disposable output.
- **Don't duplicate the Graph.** Mail, meetings, chats live where they live; both tools query them in place.

## Governance rules (Crown corporation — these are hard rules)

1. **Author-only content.** The repo contains what *you* wrote: your notes, your distilled research, your item logs. Never bulk-copy colleagues' chats, emails, shared OneNotes, or meeting transcripts into it — even ones you can legitimately read. Copying pulls content out from under DLP, retention, and sensitivity labels; querying it live via sanctioned connectors is the compliant path. (An Ontario Auditor General report on unsanctioned AI use in government is the cautionary tale — and the strongest argument for your role existing.)
2. **Reference facts vs. work data.** "Luna costs $X (public pricing page)" is a fact — fine anywhere. "Our Q3 gas volume forecast" is work data — work instance only, never the home template, never personal GitHub.
3. **Every automation you run is a future policy question.** You're the person who'll write the org's rules for this; run your own system the way you'd defend it in an audit: sanctioned connectors, delegated permissions, no scraping, sources cited.
4. **When in doubt, this system is your best demo.** "Here's how I run my own work — governed, auditable, compounding" is the most credible enablement pitch you'll ever give a skeptical team. Practice-what-you-preach is the product.

## Keeping template and instance in sync

- **System improvements** (better prompt, new doc, refined CLAUDE.md) — make them in whichever copy you're in, port the *file* to the other side when convenient. They're generic by construction.
- **Content** (worklogs, reference facts, items) — never syncs. Two instances, two worlds.
- A quarterly 15-minute "port sweep" — diff `prompts/` and `docs/` between copies — is plenty.
