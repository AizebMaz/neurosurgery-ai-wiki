---
title: Claude Code Hooks
created: 2026-04-07
last-updated: 2026-04-07
status: growing
source-docs: ["video-7huCP6RkcY4-notes.md"]
---

# Claude Code Hooks

Automated triggers in Claude Code that enable the [[compounding-loop|compounding loop]] for knowledge base construction. Based on [[video-7huCP6RkcY4-notes|the video]] at (8:40).

## Purpose

Hooks intercept key session events to:
- Capture conversation history
- Summarize learnings automatically
- Maintain the knowledge base without manual intervention

## Hook Types

### Session Start Hook — (12:44)

**Triggers**: When a new Claude Code session begins

**Actions**:
- Loads `agents.mmd` — Defines agent role and behavior
- Loads `index.mmd` — Agent understands knowledge base structure
- Initializes context for the session

**Result**: Agent starts with full context of the knowledge base.

### Pre-compact Hook — (14:51)

**Triggers**: Before memory compaction occurs

**Actions**:
- Intercepts chat history before it's compressed
- Captures full conversation context
- Prepares for summarization

### Session End Hook — (14:51)

**Triggers**: When session closes

**Actions**:
- Captures complete conversation transcript
- Sends to LLM for summarization
- Extracts: decisions, lessons learned, action items (15:03-15:20)
- Saves to daily log file (15:35-15:42)

## The Flow

```
Session Start: Load context
     ↓
Work happens (questions, coding, analysis)
     ↓
Pre-compact/Session End: Capture → Summarize → Log
     ↓
[Time passes]
     ↓
Flush: Daily logs → Wiki compilation
     ↓
Next Session Start: Load updated context
```

## Configuration

Hooks are configured in `.claude/settings.json`:

```json
{
  "hooks": {
    "SessionStart": ["load-agents", "load-index"],
    "PreCompact": ["capture-transcript"],
    "SessionEnd": ["summarize-and-log"]
  }
}
```

## Benefits

1. **Automation**: No manual work to maintain knowledge base
2. **Completeness**: Captures all sessions, not just notable ones
3. **Timeliness**: Fresh context immediately available
4. **Scalability**: Works across many sessions without overhead

## Requirements

- Claude Code with hooks support
- Claude Agent SDK for summarization
- File system access for logging
- Scheduled flush process (daily recommended)

## See Also

- [[compounding-loop|Compounding Loop]]
- [[claude-agent-sdk|Claude Agent SDK]]
- [[claude-memory-compiler|claude-memory-compiler]]
