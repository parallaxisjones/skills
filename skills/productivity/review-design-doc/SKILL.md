---
name: review-design-doc
description: Review a Notion design doc and save the review to the Obsidian Encounters inbox. Emphasis on technical critique — hidden assumptions, scale and failure modes, data and security gaps. Compares structure against a baseline template but only flags what actually matters. Use when the user gives a Notion URL and asks to review a design doc, do a design review, or critique a design.
---

# Review Design Doc

Read a Notion design doc, find what matters, write the review to the Obsidian vault.

## Input

A Notion URL (page or share link).

## Output

A new note at `~/Documents/notes/+ Encounters/Design Review - <doc title>.md` with Obsidian frontmatter, a link back to the Notion source, and findings grouped by severity.

## Workflow

1. **Fetch the doc** with the Notion MCP `notion-fetch` tool. If it resolves to a database, ask the user which page.

2. **Read the rubric** in [RUBRIC.md](RUBRIC.md). That's the baseline template structure. Don't quote it back at the user — use it as a checklist in your head to notice what's missing.

3. **Review with emphasis on technical critique.** Look hardest for:
   - Hidden assumptions — what does the design quietly take for granted? Does it hold?
   - Scale / failure modes — what at 10×? What when a dependency is down?
   - Data ownership & consistency — who writes, who reads, races, eventual-consistency surprises
   - Security & privacy — PII flow, auth boundaries, blast radius of a leak
   - Operational gaps — observability, rollback, on-call handoff
   - Risks the author named — are the mitigations real or hand-waves?
   - Alternatives — actually compared, or asserted?

4. **Only-when-it-matters rule.** Do NOT produce a section-by-section ✓/✗ of the rubric. Only flag a missing or thin section when its absence creates real ambiguity, risk, or an unanswered question. Examples:
   - Missing Non-Goals on an ambiguous scope → flag
   - Missing Non-Goals on a clearly bounded fix → skip
   - Missing Risks → almost always flag
   - Missing Localization on an internal tool → skip
   - Missing Alternatives on a decision with obvious tradeoffs → flag
   - Missing Alternatives on a routine implementation → skip

5. **Group findings by severity:**
   - **Blockers** — must resolve before sign-off
   - **Important** — should resolve, design can proceed in parallel
   - **Nits / suggestions** — author's call

   Omit any severity section that has no findings. No empty headings.

6. **Write the note** in the format below. Save to `~/Documents/notes/+ Encounters/Design Review - <title>.md` (spaces in filename are fine for Obsidian).

7. **Report back** — clickable path to the new note, plus one sentence on the worst finding.

## Note format

```md
---
created: <YYYY-MM-DD HH:MM>
type: design-review
domain: work
status: active
tags:
  - design-reviews
  - encounters
source: <Notion URL>
---

# Design Review — <Doc Title>

**Doc**: [<Doc Title>](<Notion URL>)
**Reviewed**: <YYYY-MM-DD>

## Summary

<1–2 sentence neutral summary of what the doc proposes. No verdict.>

## Blockers

- **<Finding title>** — what's wrong, why it matters, suggested resolution.

## Important

- **<Finding title>** — same shape.

## Nits / suggestions

- **<Finding title>** — same shape.

## Related

- [[<related note>]]
```

## Vault conventions

- Wikilinks have no `.md`: `[[note-title]]`, never `[[note-title.md]]`.
- Tags are plural, may be nested (`design-reviews`, `work/projects`).
- `created` is local time, `YYYY-MM-DD HH:MM`.
- Before writing the `## Related` section, search the vault for notes whose titles match domain terms in the doc (project name, system, feature). Only include real hits — don't invent links.

## When the doc is a stub

If it's clearly mid-draft, say so in the Summary and ask the user whether to review what's there or wait. Don't pile findings onto a doc that isn't ready.
