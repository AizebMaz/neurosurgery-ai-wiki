# LLM Wiki: Neurosurgery & AI Development

This file defines the schema and conventions for this wiki.

## Purpose

A persistent, compounding knowledge base bridging neurosurgical domain knowledge with AI/ML development practices. The wiki is maintained by an LLM agent (Claude) through explicit operations.

## Directory Structure

```
/
├── CLAUDE.md          # This file: conventions and schema
├── index.md           # Catalog of all pages with summaries
├── log.md             # Append-only chronological record
├── sources/           # Raw source documents (immutable)
└── wiki/              # Generated markdown pages
    ├── neurosurgery/  # Neurosurgical domain knowledge
    ├── ai-dev/        # AI/ML development practices
    └── integration/   # Cross-domain connections
```

## Page Conventions

### Naming
- Use `kebab-case.md` for filenames
- Prefer concrete nouns over abstractions (e.g., `craniotomy-approaches.md` not `surgery-concepts.md`)

### Frontmatter
Every wiki page must include:

```yaml
---
title: Page Title
created: YYYY-MM-DD
last-updated: YYYY-MM-DD
status: seed|growing|mature
source-docs: ["source-filename.pdf", "paper-doi"]
---
```

- `seed`: Just created, minimal content
- `growing`: Substantial content, may have gaps
- `mature`: Comprehensive, well-linked, reviewed

### Cross-References
- Use Obsidian-style wiki links: `[[page-name]]`
- Always create backlinks when adding a forward link
- Link liberally—pages should be densely connected

## Operations

### Ingest
1. Read raw source from `sources/`
2. Create/update 10-15 wiki pages
3. Update `index.md` with new pages
4. Append to `log.md` with `## [YYYY-MM-DD] ingest: [source-name]`

### Query
1. Synthesize answer from wiki pages
2. If answer reveals gaps, create stub pages
3. If answer is novel, append to `log.md` with `## [YYYY-MM-DD] query: [question-summary]`

### Lint
1. Check for orphan pages (no incoming links)
2. Check for contradictions between pages
3. Check for broken wiki links
4. Append findings to `log.md` with `## [YYYY-MM-DD] lint: [findings]`

## Content Guidelines

### Neurosurgery Pages
- Include anatomical coordinates (when relevant)
- Distinguish between approaches, indications, and complications
- Link procedures to relevant AI applications

### AI Development Pages
- Include code patterns and architectural decisions
- Link techniques to neurosurgical use cases
- Note data privacy and regulatory considerations

### Integration Pages
- Explicitly bridge neurosurgical concepts with AI methods
- Document domain-specific adaptations of general AI techniques
- Track translational opportunities

## Log Format

```markdown
## [YYYY-MM-DD] operation-type: brief-description

Details...
- Point 1
- Point 2

Links: [[related-page-1]], [[related-page-2]]
---
```

Operations: `ingest`, `query`, `lint`, `create`, `update`, `merge`, `split`

## Review Checklist

Before marking a page `mature`:
- [ ] All claims have sources cited
- [ ] At least 3 incoming wiki links
- [ ] At least 3 outgoing wiki links
- [ ] Summary in `index.md` is accurate
- [ ] No TODO markers remain
