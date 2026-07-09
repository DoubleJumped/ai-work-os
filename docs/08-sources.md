# 08 — Sources and further reading

This system's design decisions came from a four-track research pass (2026-07-09). The load-bearing sources, by decision:

## Role model: forward-deployed engineering + AI enablement

- **Palantir FDE model** — the embed-4-days / platform-1-day split; discovery as core engineering work (~30–40% of the week); "ship in week one," no throwaway prototypes; and the flywheel: every engagement's solution gets encoded as a reusable platform primitive. https://blog.palantir.com/a-day-in-the-life-of-a-palantir-forward-deployed-software-engineer-45ef2de257b1 · https://newsletter.pragmaticengineer.com/p/forward-deployed-engineers
- **Microsoft Cloud Adoption Framework — "Establish an AI CoE"** — a ready-made charter: seven responsibilities including intake/prioritization; start centralized, evolve to advisory; attach to existing teams rather than standalone. https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/center-of-excellence
- **Anthropic enterprise deployment playbook** — pilot 50–100 users, 2–3 champions per department; benchmarks: 70% weekly active, 3+ hrs saved/user/week. https://claude.com/resources/tutorials/claude-enterprise-administrator-guide
- **BCG 10-20-70** — 70% of AI effort is people/process/culture, 20% data/tech, 10% models. The antidote to over-building. https://www.bcg.com/publications/2026/reinventing-the-operating-system-of-work-with-ai
- **Failure modes for one-person functions** — becoming the approval bottleneck; context living in one head; pilots that don't survive scaling. Antidotes: champions, the shared library, pilots as miniature production systems.

## The Velocity Whitepapers (Government of Alberta, July 2026)

The closest published analog to this role: a government's open-sourced playbook for AI-driven modernization. https://thevelocitywhitepapers.com/ — read first:

- **The Well-Built Harness** — curated templates + standards + review agents so anyone's AI output converges on compliant results; never let AI author the harness itself. https://thevelocitywhitepapers.com/paper/p7p2k/
- **The AI Academy** — the **"rule of three"**: anything done 3+ times/week becomes a shared reusable agent. This repo's compounding mechanism, made teachable. https://thevelocitywhitepapers.com/paper/dt725/
- **Measuring Failure and Success** — the three-pillar scorecard (Readiness / System Health / Cost) this roadmap uses. https://thevelocitywhitepapers.com/paper/yu5k9/
- **The Shape of Data** — "the pipeline is the part that matters"; auditability as the differentiator. https://thevelocitywhitepapers.com/paper/wq3kd/
- Anthropic's case study on the program: https://www.anthropic.com/news/alberta-government-claude-cybersecurity
- **Caution:** the headline numbers (95% reductions, "1 agent ≈ 20 workers") are first-party and unaudited. Borrow the frameworks confidently; present the numbers as "Alberta's reported results, to validate in our own pilots."

## Roadmap format and upward communication

- **Now/Next/Later** (Janna Bastow/ProdPad) — why undated beats Gantt for the exec altitude. https://www.prodpad.com/blog/invented-now-next-later-roadmap/ · https://www.aakashg.com/now-next-later-roadmap/
- **Platform vs product roadmaps** — different horizons, one story: platform items always framed as enablers of named outcomes. https://www.aha.io/blog/the-product-roadmap-vs-the-platform-roadmap
- **Platform as a Product** (Team Topologies) — internal platforms must market their value or lose funding. https://teamtopologies.com/platform-engineering
- **One-page AI strategy** (Superhuman's 4-box: problem / smallest viable solution / 30-day proof / one metric that matters). https://blog.superhuman.com/ai-strategy-roadmap/
- **PowerPoint as lingua franca** — why dashboards/HTML die upward ("within six weeks the CEO is back to asking for a PowerPoint summary") and the HTML→PPTX escape hatch. https://gitbrent.github.io/PptxGenJS/docs/html-to-powerpoint/
- **Amazon narrative pre-reads** — short written memos beat slide decks for quarterly reviews. https://www.anecdote.com/2018/05/amazons-six-page-narrative-structure/

## Capture, rollup, and the M365/Claude split

- **Brag documents** (Julia Evans) — the canonical case for durable self-record. https://jvns.ca/blog/brag-documents/
- **Work log template** (Pragmatic Engineer). https://blog.pragmaticengineer.com/work-log-template-for-software-engineers/
- **Interstitial journaling** — capture at the task switch because it *reduces* in-the-moment effort. https://nesslabs.com/interstitial-journaling
- **Copilot weekly-summary prompt** (Microsoft's own "review my inbox, calendar and Teams activity from the past seven days" format). https://news.microsoft.com/signal/articles/prompt-microsoft-365-copilot-weekly-work-summary-manager-meetings/
- **Copilot Scheduled Prompts** — native recurring prompts, up to 10/user, requires the Copilot add-on license. https://learn.microsoft.com/en-us/copilot/microsoft-365/scheduled-prompts
- **Copilot does not index .md** — the constraint behind the .docx mirror. https://techcommunity.microsoft.com/discussions/microsoft365copilot/markdown-dateien--md-in-copilot-for-onedrive--graph-data-connect/4459944
- **Cowork scheduled tasks** — cloud-run, hence the OneDrive requirement. https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-claude-cowork
- **Microsoft 365 connector for Claude** — sanctioned read-only Graph access; needs tenant admin consent. https://support.claude.com/en/articles/12684923-microsoft-365-connector-security-guide
- **Oversharing / governance** — why "query live, never copy out" is the rule. https://learn.microsoft.com/en-us/copilot/privacy-and-protections
- **Ontario AG audit on shadow AI in government** — the Crown-corp cautionary tale. https://www.auditor.on.ca/en/content/specialreports/specialreports/en26/2026_AI_EN.pdf

## Sector references

- **Ontario Power Generation — ChatOPG** — the closest published utility analog (internal assistant for procedures, safety protocols, troubleshooting). https://www.microsoft.com/en-us/industry/blog/energy-and-resources/2023/05/04/microsoft-highlights-innovation-in-power-and-utilities/
- **EPRI / Open Power AI Consortium** — sector body worth tracking. https://blogs.nvidia.com/blog/open-power-ai-consortium/
