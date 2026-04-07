---
title: LLM Wiki Methodology
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["ai-2027-article.md", "claude-memory-compiler.md", "video-7huCP6RkcY4-notes.md"]
---

# LLM Wiki Methodology

An approach to knowledge management where an LLM maintains structured markdown pages rather than retrieving raw chunks. Inspired by Andrej Karpathy's "LLM Knowledge Base" concept and implemented in tools like [[claude-memory-compiler|claude-memory-compiler]].

## Core Idea

Traditional RAG (Retrieval-Augmented Generation):
- Chunk documents
- Embed chunks into vectors
- Retrieve similar chunks at query time
- LLM synthesizes answer from chunks

LLM Wiki approach:
- LLM reads full source documents
- Creates structured, interlinked markdown pages
- Maintains index for navigation
- LLM reads wiki pages (not raw chunks) to answer questions
- Compounds over time as wiki grows

## Why It Works

### At Personal Scale
"At personal scale (50-500 articles), the LLM reading a structured index.md outperforms vector similarity."

— [[video-7huCP6RkcY4-notes|Video source]] (citing [Karpathy X thread](https://x.com/karpathy/thread/2039805659525644595))

- LLMs excel at understanding structured markdown
- Cross-references provide explicit relationships
- Index enables efficient navigation
- Human-readable format allows verification

### Compounding Benefits
- Each ingestion adds to persistent knowledge
- Wiki pages get cross-linked
- Index grows more useful over time
- Agent learns your domain

## Architecture

### Three Layers
1. **Raw sources** (immutable documents in `sources/`)
2. **The wiki** (LLM-generated markdown with cross-references in `wiki/`)
3. **The schema** (conventions in `CLAUDE.md`)

### Key Files
- `CLAUDE.md` — Schema and conventions
- `index.md` — Content catalog with summaries
- `log.md` — Append-only chronological record
- `wiki/*.md` — Interconnected pages

## Operations

### Ingest
1. Add raw source to `sources/`
2. LLM creates/updates 10-15 wiki pages
3. Update `index.md`
4. Append to `log.md`

### Query
1. LLM synthesizes from wiki pages
2. Reveals gaps → create stubs
3. Novel insights → append to `log.md`

### Lint
1. Check for orphan pages (no incoming links)
2. Check for contradictions
3. Check for broken links
4. Log findings

## Page Conventions

### Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
last-updated: YYYY-MM-DD
status: seed|growing|mature
source-docs: ["source-file.md"]
---
```

### Cross-References
- Use `[[page-name]]` wiki links
- Create backlinks
- Link liberally

### Status Levels
- `seed` — Just created
- `growing` — Substantial content
- `mature` — Comprehensive, well-linked

## Tools

### Viewers
- [[obsidian|Obsidian]] — Recommended for wiki links and graph view
- Any markdown editor

### Implementations
- [[claude-memory-compiler|claude-memory-compiler]] — Automated compilation from conversation hooks
- Manual wiki maintenance (this wiki)

## Comparison to Alternatives

| Approach | Pros | Cons |
|----------|------|------|
| LLM Wiki | Compounds, structured, interpretable | Requires maintenance |
| Vector RAG | Simple setup, scales to millions | Doesn't compound, retrieval errors |
| Notes manually | Full control | Human maintenance burden |

## Best Practices

- Start with seed pages, grow over time
- Cross-link aggressively
- Maintain the index
- Review and lint periodically
- Use Obsidian for visualization

## See Also

- [[claude-memory-compiler|claude-memory-compiler]] — Automated implementation
- [[karpathy-llm-knowledge-base|Karpathy's LLM Knowledge Base]] — Original concept
- [[llm-knowledge-compiler|LLM Knowledge Compiler]] — Five-stage compiler architecture
- [[compounding-loop|Compounding Loop]] — Self-reinforcing knowledge growth
- [[obsidian|Obsidian]] — Recommended viewer
- This wiki uses this methodology
