# Prompt: file this research

<!-- Use at the end of any session where research happened — or paste a raw finding after it.
     CLAUDE.md already obligates agents to file as they go; this prompt is for catching strays. -->

Read CLAUDE.md. File the research from this session (or the notes below) into the repo:

1. Distill to answer-shaped facts. Stable facts vs volatile facts; volatile ones get `(as of YYYY-MM-DD, source: url)`.
2. Check `reference/INDEX.md` for an existing file on the topic — update in place (supersede, don't append) or create from `reference/_template.md`. Update the index in the same action.
3. If any fact changes an assumption on a roadmap or intake item, add a dated `[ref]` line to that item's `## Log` naming the reference file and the implication.
4. Add the `[ref]`-tagged line to today's worklog.
5. Reply with: files touched, facts filed, and any item whose assumptions changed.
