---
title: Knowledge Base Health Checks
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["video-7huCP6RkcY4-notes.md"]
---

# Knowledge Base Health Checks

A process for maintaining data integrity in an LLM wiki, compared to "linting code" in [[video-7huCP6RkcY4-notes|the video]] at (4:37).

## Purpose

Ensure the knowledge base remains:
- **Navigable** — All links work
- **Complete** — No gaps between raw and wiki
- **Accurate** — No stale or contradictory information
- **Growing** — Knowledge gaps identified for future research

## Health Check Operations

### 1. Broken Link Detection — (4:55)

Scans wiki documentation to identify:
- Wiki links pointing to non-existent pages
- References to missing concepts
- Orphaned expected targets

**Fix**: Create missing pages or remove broken links.

### 2. Data Integrity Checks — (4:40-5:00)

Identifies discrepancies:

| Check | Issue | Action |
|-------|-------|--------|
| **Stale raw files** | Files in `sources/` not yet in wiki | Run ingest |
| **Orphan pages** | Wiki pages with no incoming links | Create backlinks or merge |
| **Knowledge gaps** | Topics referenced but not documented | Flag for research |
| **Contradictions** | Inconsistent information across pages | Reconcile and update |

### 3. Freshness Audit

Reviews pages for:
- Outdated information (check `last-updated` date)
- Superseded by newer sources
- Status that no longer matches content (`seed` vs `mature`)

## Comparison to Code Linting

| Code Linting | Knowledge Linting |
|--------------|-------------------|
| Syntax errors | Broken wiki links |
| Unused variables | Orphan pages |
| Style violations | Status mismatches |
| Dead code | Stale sources not in wiki |
| Missing imports | Knowledge gaps |

## Running Health Checks

### Manual
- Review `index.md` for completeness
- Check log for reported issues
- Use Obsidian graph view to spot orphans

### Automated
- Scripts scan for broken `[[links]]`
- Compare `sources/` to `wiki/` coverage
- Validate frontmatter dates and status

## Example Output

```
Health Check Results:
- 2 broken links found: [[neurosurgery-basics]], [[deep-learning-history]]
- 3 stale raw files: sources/paper-2019.md (not in wiki)
- 1 orphan page: wiki/ai-dev/old-concept.md (0 incoming links)
- 2 knowledge gaps: "surgical robotics", "fMRI analysis"
```

## Integration with Workflow

Health checks should run:
- After each ingest operation
- Periodically (weekly) for maintenance
- Before important queries (ensure completeness)

## See Also

- [[llm-knowledge-compiler|LLM Knowledge Compiler]]
- [[llm-wiki-methodology|LLM Wiki Methodology]]
- [[index|Index]] — Check here first for completeness
