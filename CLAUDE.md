# Second Brain — LLM Wiki Schema

This file governs how the LLM agent operates in this vault. Read it at the start of every session.

---

## Directory Layout

```
Second Brain/
├── CLAUDE.md           ← this file (schema + operating instructions)
├── raw/                ← immutable source documents (human writes, LLM reads only)
│   └── assets/         ← locally downloaded images referenced by sources
├── wiki/               ← LLM-maintained knowledge base (LLM writes, human reads)
│   ├── index.md        ← content catalog (updated on every ingest)
│   ├── log.md          ← chronological log (newest entry first)
│   ├── overview.md     ← high-level synthesis across all sources
│   ├── sources/        ← one summary page per ingested source
│   ├── entities/       ← people, organizations, places, products
│   └── concepts/       ← ideas, themes, frameworks, topics
```

**Rule:** The LLM never modifies files in `raw/`. Everything in `wiki/` is LLM-owned.

---

## Page Frontmatter

Every wiki page (except index.md and log.md) must start with YAML frontmatter:

```yaml
---
title: "Page Title"
type: source | entity | concept | overview | analysis
tags: [tag1, tag2]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: 0        # number of source pages this draws from (omit for source pages)
---
```

---

## Operations

### 1. INGEST

Triggered when the user says: "ingest [file]", "process [file]", or drops a new file in `raw/`.

**Steps (in order):**
1. Read the source file in `raw/`.
2. If images are referenced, read them separately for visual context.
3. Discuss key takeaways with the user — what's most important, surprising, or useful.
4. Write a summary page in `wiki/sources/` (see Source Page Format below).
5. Create or update entity pages in `wiki/entities/` for any named persons, orgs, places, products.
6. Create or update concept pages in `wiki/concepts/` for key ideas and themes.
7. Update `wiki/overview.md` to reflect any shifts in the overall synthesis.
8. Update `wiki/index.md` — add the new source, update any touched pages.
9. Prepend a new entry at the top of `wiki/log.md` (below the header and first `---`).

**Source Page Format** (`wiki/sources/<slug>.md`):
```markdown
---
title: "Source Title"
type: source
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
raw: "raw/filename.md"
---

## Summary
2–4 paragraph synthesis of the source.

## Key Claims
- Bullet list of the most important claims, data points, or arguments.

## Entities
Links to entity pages touched by this source: [[Entity Name]], ...

## Concepts
Links to concept pages touched by this source: [[Concept Name]], ...

## Contradictions & Tensions
Note any claims that conflict with existing wiki pages. Link to the affected pages.

## Open Questions
Questions this source raises that are not yet answered in the wiki.
```

**Entity Page Format** (`wiki/entities/<slug>.md`):
```markdown
---
title: "Entity Name"
type: entity
tags: [person | org | place | product]
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: N
---

## Overview
1–2 sentence description.

## Key Facts
- Factual bullets, each citing a source: [[source-slug]]

## Appearances
List of source pages where this entity appears: [[source-slug]], ...

## Related
Links to related entities and concepts.
```

**Concept Page Format** (`wiki/concepts/<slug>.md`):
```markdown
---
title: "Concept Name"
type: concept
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: N
---

## Definition
Clear, concise definition as understood from the sources.

## Evidence & Examples
Concrete examples from sources, each cited: [[source-slug]]

## Counter-evidence & Tensions
Where sources disagree or complicate the concept.

## Related Concepts
[[Concept A]], [[Concept B]]

## Sources
[[source-slug-1]], [[source-slug-2]], ...
```

---

### 2. QUERY

Triggered when the user asks a question about the wiki's content.

**Steps:**
1. Read `wiki/index.md` to identify relevant pages.
2. Read the relevant pages.
3. Synthesize an answer with inline citations linking to wiki pages.
4. Ask the user: "Should I save this as a wiki page?" If yes, write it to `wiki/` under the appropriate category as `type: analysis`.

---

### 3. LINT

Triggered when the user says: "lint the wiki", "health check", or "audit".

**Check for:**
- Contradictions between pages (flag specific pages and claims)
- Orphan pages (no inbound links from other wiki pages)
- Mentioned concepts or entities with no dedicated page
- Stale claims superseded by newer sources
- Missing cross-references between obviously related pages
- Data gaps worth filling (suggest specific sources to seek)

**Output:** A markdown report. Ask the user whether to file it as a wiki page.

---

### 4. SESSION START

At the beginning of every session:
1. Read this file (CLAUDE.md).
2. Read `wiki/index.md`.
3. Read the first 10 entries in `wiki/log.md`.
4. Briefly tell the user the current state: how many sources, last ingested, any open questions flagged in the log.

---

## Index Format (`wiki/index.md`)

Sections: Sources, Entities, Concepts, Analyses. Each entry: `- [[page-link]] — one-line description (YYYY-MM-DD)`.

## Log Format (`wiki/log.md`)

Each entry: `## [YYYY-MM-DD] <operation> | <title>` followed by 1–3 bullet points.
Operations: `ingest`, `query`, `lint`, `update`.

New entries go at the top (newest first). Never delete or edit past entries.

---

## Style Rules

- All wiki pages are in English unless the user specifies otherwise.
- Keep summaries dense and factual. No filler.
- Always create wiki links (`[[Page Name]]`) for entities and concepts the first time they're mentioned on a page.
- Slugs are lowercase, hyphen-separated: `john-doe.md`, `network-effects.md`.
- When a source contradicts an existing claim, update the relevant page and note the tension — do not silently overwrite.
- If a page would be a stub (< 3 useful bullets), note it as a stub in frontmatter: `stub: true` and return to it when more sources support it.
- **Never write a `[[wikilink]]` unless the target file already exists or will be created in the same operation.** Unresolved links create empty ghost pages in Obsidian when clicked. When referencing a concept inline without a dedicated page, write it as plain text instead of a wikilink.
- **Never split a compound concept into separate wikilinks.** Example: write `[[construir-medir-aprender]]`, never `[[Construir]]`, `[[Medir]]`, `[[Aprender]]` as three separate links.

---

## Scope

This is a personal second brain. The user decides the domain. The LLM maintains discipline, consistency, and cross-referencing. The human decides what to read and what matters.

---

## gstack

Use the `/browse` skill from gstack for all web browsing. Never use `mcp__claude-in-chrome__*` tools.

Available gstack skills:
`/office-hours`, `/plan-ceo-review`, `/plan-eng-review`, `/plan-design-review`, `/design-consultation`, `/design-shotgun`, `/design-html`, `/review`, `/ship`, `/land-and-deploy`, `/canary`, `/benchmark`, `/browse`, `/connect-chrome`, `/qa`, `/qa-only`, `/design-review`, `/setup-browser-cookies`, `/setup-deploy`, `/setup-gbrain`, `/retro`, `/investigate`, `/document-release`, `/document-generate`, `/codex`, `/cso`, `/autoplan`, `/plan-devex-review`, `/devex-review`, `/careful`, `/freeze`, `/guard`, `/unfreeze`, `/gstack-upgrade`, `/learn`
