---
title: LLM Knowledge Compiler
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["video-7huCP6RkcY4-notes.md"]
---

# LLM Knowledge Compiler

The LLM Personal Knowledge Base system functions like a **software compiler for human knowledge** ([[video-7huCP6RkcY4-notes|source]]). Instead of using complex vector databases, it uses an Obsidian vault to manage raw data, which is then processed by an LLM into a structured, interconnected wiki.

## The Five Stages

```
Raw Sources → Compiler (LLM) → Wiki (Executable) → Health Checks → Runtime (Query)
```

### 1. Data Ingestion (The Raw Folder)

**Timestamp: (3:11)**

The entry point. You dump raw Markdown files into a dedicated folder:
- Articles
- Research papers
- Transcripts
- Notes

This is your immutable source material.

### 2. The Compiler Stage (LLM Processing)

**Timestamp: (3:23)**

Scripts feed raw data into an LLM which analyzes content to:
- **Generate summaries** — Distill key points
- **Extract key concepts** — Identify important entities and ideas
- **Interlink documents** — Create bidirectional wiki links between related content

This is the transformation step where raw data becomes structured knowledge.

### 3. The Executable (The Wiki)

**Timestamp: (3:47)**

The compiler outputs a structured wiki folder — the version you actually query. Contains:

| Component | Purpose | Timestamp |
|-----------|---------|-----------|
| **Concepts** | Synthesized information from sources | (6:48) |
| **Connections** | Metadata mapping relationships | (7:00) |
| **Index** | High-level table of contents | (5:32) |

### 4. Health Checks (The Test Suite)

**Timestamp: (4:37)**

Similar to linting code — ensures data integrity:
- **Identify knowledge gaps** — Where further research needed
- **Clean stale data** — Raw files not yet in wiki
- **Fix broken links** — Maintain clean graph structure (4:55)

See [[knowledge-base-health-checks|detailed page]].

### 5. The Runtime (Querying)

**Timestamp: (5:12)**

Because the LLM maintains a clean, index-driven file structure, **you do not need complex RAG** (Retrieval-Augmented Generation). Your AI agent traverses the Markdown files directly based on the index to provide context-aware answers (5:45).

## Why This Works

> "At personal scale (50-500 articles), the LLM reading a structured index.md outperforms vector similarity."

- LLMs excel at understanding structured markdown
- Cross-references provide explicit relationships
- Index enables efficient navigation
- Compounds over time

## Comparison: Compiler vs. RAG

| Aspect | LLM Compiler | Vector RAG |
|--------|--------------|------------|
| Processing | Batch (compile step) | Real-time (retrieve) |
| Structure | Explicit links | Implicit similarity |
| Maintenance | Lint/fix | Re-index |
| Scale | 50-500 articles | Millions of chunks |
| Compounding | Yes | No |

## See Also

- [[llm-wiki-methodology|LLM Wiki Methodology]]
- [[knowledge-base-health-checks|Knowledge Base Health Checks]]
- [[compounding-loop|Compounding Loop]]
- [[obsidian|Obsidian]]
