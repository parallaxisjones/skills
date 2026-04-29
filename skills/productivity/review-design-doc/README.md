# review-design-doc

Review a Notion design doc with emphasis on technical critique. Saves the review as an Obsidian note in `~/Documents/notes/+ Encounters/`.

## What it does

Given a Notion URL, the skill:

1. Fetches the page via the Notion MCP `notion-fetch` tool.
2. Compares the doc's structure against [RUBRIC.md](RUBRIC.md) — a baseline design-doc template — but only flags missing sections when their absence creates real ambiguity or risk. No section-by-section ✓/✗ checklist.
3. Reviews with emphasis on technical critique: hidden assumptions, scale and failure modes, data ownership and consistency, security, operational gaps, hand-wavy risk mitigations, asserted-not-compared alternatives.
4. Writes findings grouped by severity — **Blockers / Important / Nits** — and omits empty severity sections.
5. Saves the review at `~/Documents/notes/+ Encounters/Design Review - <doc title>.md` with vault-conventional frontmatter and a link back to the Notion source.

## How to invoke

```
/review-design-doc <notion-url>
```

Or just paste a Notion URL and ask for a design review.

## Files

- [SKILL.md](SKILL.md) — agent instructions, workflow, output format
- [RUBRIC.md](RUBRIC.md) — baseline design-doc template, annotated with what's worth flagging when absent

## Output conventions

- Wikilinks have no `.md` extension
- Tags are plural and may be nested
- `created` frontmatter is local time, `YYYY-MM-DD HH:MM`
- Filename prefix `Design Review - ` so they group together in Obsidian search

## Customizing

The two most likely places to tune behavior:

- **What gets flagged** — `RUBRIC.md` "Watch for" / "flag when missing" notes
- **Note format** — the markdown template in `SKILL.md` under "Note format"
