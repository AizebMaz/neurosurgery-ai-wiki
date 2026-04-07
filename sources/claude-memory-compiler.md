# claude-memory-compiler

Source: https://github.com/coleam00/claude-memory-compiler
Date ingested: 2026-04-07

---

## Overview

A system that gives "Claude Code a memory that evolves with your codebase."

## How It Works

### Automatic Capture
Hooks automatically capture conversation transcripts when sessions end or compact.

### Background Processing
Uses "the Claude Agent SDK to extract the important stuff - decisions, lessons learned, patterns, gotchas" and appends these to daily logs.

### Compilation
The `compile.py` script transforms logs into structured articles organized under:
- `knowledge/concepts/` - Core ideas
- `connections/` - Relationships between concepts
- `qa/` - Question-answer pairs

### Session Initialization
A SessionStart hook injects the knowledge index into new conversations.

## Memory Approach

Rather than vector databases, the system relies on "a simple index file instead of RAG - no vector database, no embeddings, just markdown."

Following "Karpathy's LLM Knowledge Base" architecture, it avoids traditional retrieval because "at personal scale (50-500 articles), the LLM reading a structured index.md outperforms vector similarity."

## Key Philosophy

- Markdown-based knowledge base
- Structured organization (concepts, connections, qa)
- Index file for navigation
- LLM-maintained, not vector-retrieved
- Compounds over time

## Usage

Install via `uv sync`, activate hooks by copying `.claude/settings.json`, then run:
- `uv run python scripts/compile.py` to compile logs
- `uv run python scripts/query.py "question"` to search

## Technical Notes

Anthropic confirms "personal use of the Claude Agent SDK is covered under your existing Claude subscription."
