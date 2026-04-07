---
title: Compounding Loop
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["video-7huCP6RkcY4-notes.md"]
---

# Compounding Loop

The self-reinforcing cycle where the knowledge base grows smarter over time as sessions accumulate, are summarized, and filed into the wiki. Described in [[video-7huCP6RkcY4-notes|the video]] at (16:51).

## The Cycle

```
Work Session → Capture → Summarize → Log → Flush → Wiki Update → Future Sessions
```

### 1. Work Session
You interact with Claude Code on tasks, problems, questions.

### 2. Capture (14:51-14:58)
Whenever you close a session or trigger memory compaction, **hooks** intercept the chat history:
- Pre-compact hooks
- Session-end hooks

### 3. Summarize (15:03-15:20)
Raw transcript sent to LLM (via Claude Agent SDK) extracts:
- **Decisions made** — What was chosen
- **Lessons learned** — Insights gained
- **Action items** — Next steps

### 4. Create Daily Logs (15:35-15:42)
Summaries saved into daily log files — these become the 'raw' material for the knowledge base.

### 5. The Flush (15:52-16:04)
Once a day, the system:
- Analyzes logs for recurring concepts
- Identifies connections between ideas
- Compiles into Obsidian vault's wiki folder

### 6. Future Reference (16:51-17:28)
The agent can now reference past lessons in future sessions:
- `index.mmd` file is active and searchable
- Agent builds upon stored information
- Knowledge base becomes **smarter over time**

## Why It Compounds

| Session | Knowledge Base State |
|---------|---------------------|
| 1 | Base + Session 1 learnings |
| 2 | Base + S1 + S2 learnings + connections between S1→S2 |
| 3 | Base + S1 + S2 + S3 + connections S1↔S2↔S3 |
| n | All prior sessions + all interconnections |

Each session adds:
- New raw content
- New synthesized concepts
- New connections to existing knowledge
- Better context for future queries

## Key Insight

> "As you continue to work, the agent builds upon this stored information, effectively making your knowledge base smarter over time."

The knowledge base is not just a static repository — it's an **active participant** that improves your future work.

## Implementation Requirements

- **Hooks**: SessionStart, Pre-compact, Session-end
- **Claude Agent SDK**: For summarization
- **Daily log format**: Structured raw material
- **Flush process**: Periodic compilation
- **Index file**: Keeps wiki navigable

## See Also

- [[claude-code-hooks|Claude Code Hooks]]
- [[claude-agent-sdk|Claude Agent SDK]]
- [[llm-knowledge-compiler|LLM Knowledge Compiler]]
- [[llm-wiki-methodology|LLM Wiki Methodology]]
