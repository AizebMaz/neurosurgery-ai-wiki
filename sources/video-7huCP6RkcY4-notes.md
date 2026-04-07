# LLM Personal Knowledge Base (Video Notes)

Source: https://www.youtube.com/watch?v=7huCP6RkcY4
Citations: https://x.com/karpathy/thread/2039805659525644595
Date ingested: 2026-04-07

---

## Overview

The LLM Personal Knowledge Base system presented in the video (inspired by Andrej Karpathy) functions like a software compiler for human knowledge. Instead of using complex vector databases, it uses an Obsidian vault to manage raw data, which is then processed by an LLM into a structured, interconnected wiki.

## Step-by-Step Architecture

### 1. Data Ingestion (The Raw Folder) — (3:11)

This is the entry point of your system. You dump raw Markdown files—articles, research papers, transcripts, or notes—into a dedicated raw folder in your Obsidian vault.

### 2. The Compiler Stage (LLM Processing) — (3:23)

You run scripts that feed this raw data into an LLM. The model analyzes the content to:
- Generate summaries
- Extract key concepts
- Interlink documents using back-links

### 3. The Executable (The Wiki) — (3:47)

The output of the compiler is a structured wiki folder. This is the version you actually query. It contains:
- **Concepts**: Synthesized information derived from your raw sources (6:48)
- **Connections**: Metadata mapping how ideas relate to each other (7:00)
- **Index**: A central file acting as a high-level table of contents for the agent (5:32)

### 4. Health Checks (The Test Suite) — (4:37)

Similar to linting code, you perform "health checks" on your knowledge base to ensure data integrity. This involves:
- Identifying knowledge gaps where further research is needed
- Cleaning up stale data (e.g., raw files not yet in the wiki)
- Fixing broken links to maintain a clean graph structure (4:55)

### 5. The Runtime (Querying) — (5:12)

Because the LLM maintains a clean, index-driven file structure, you do not need complex RAG (Retrieval-Augmented Generation). Your AI agent traverses the Markdown files directly based on the index to provide context-aware answers (5:45).

---

## Session Logs and the Compounding Loop

The process of turning Claude Code conversation sessions into a long-term knowledge base is driven by automated hooks that treat your interaction logs as raw source data.

### Step-by-Step Flow

1. **Capturing the Data** (14:51-14:58): Whenever you close a session or trigger a memory compaction, the system uses hooks (pre-compact and session-end) to intercept the chat history.

2. **Summarization** (15:03-15:20): This raw transcript is sent to a Large Language Model (using the Claude Agent SDK) to extract actionable insights, such as decisions made, lessons learned, and action items.

3. **Creating Daily Logs** (15:35-15:42): These summaries are saved into daily log files within your workspace. These files act as the 'raw' material for your knowledge base, ensuring that context from your work isn't lost when the session ends.

4. **The Flush Process** (15:52-16:04): Once a day, the system performs a 'flush' operation where it analyzes these logs to identify recurring concepts and connections. It then compiles this information into your Obsidian vault's wiki folder.

5. **The Compounding Loop** (16:51-17:28): By structuring these insights into a searchable wiki with an active index.mmd file, the agent can reference past lessons in future sessions. As you continue to work, the agent builds upon this stored information, effectively making your knowledge base smarter over time.

---

## Role of Obsidian

In the system described, Obsidian serves as the central canvas and interface for managing your personal knowledge base (0:53). Its specific roles include:

### Data Organization
It provides the structure for the 'raw' folder where incoming information is stored, as well as the 'wiki' folder where processed, interconnected knowledge lives (3:06-3:47).

### Visualizing Knowledge
Through its graph view, it allows you to see how different pieces of information, concepts, and markdown documents are linked together, which helps the agent traverse the knowledge base more effectively (4:06-4:18).

### The 'Home' for your Second Brain
It acts as the primary environment where you view your memories and interact with the compiled wiki, making it an essential tool for maintaining your second brain (11:15-11:21).

---

## Handling Broken Data Links

The system ensures data integrity through a health check process, which the creator compares to linting code (4:37).

### Broken Link Detection
The system scans the wiki documentation to identify any instances where one document references another that does not exist (4:55).

### Data Integrity Checks
Beyond fixing broken links, the health checks help find discrepancies, such as files existing in the raw folder that have not yet been processed into the wiki, or gaps in the documentation where more research is required (4:40-5:00).

---

## Custom Implementation for Claude Code — (8:40)

To adapt this for internal codebase memory, the creator uses Claude Code hooks:

### Session Start Hook
Loads agents.mmd and the index.mmd so the agent understands its role and the structure of your knowledge base (12:44).

### Pre-compact/Session End Hooks
Automatically captures summaries of your conversations, decisions, and lessons learned into daily logs, which function as the "raw" data for future compilation (14:51).

---

## Key Quotes

- "At personal scale (50-500 articles), the LLM reading a structured index.md outperforms vector similarity."
- "Like a software compiler for human knowledge"
- "The compounding loop"
- "Your second brain"
