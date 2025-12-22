---
title: Sequential Thinking MCP
description: Dynamic problem-solving through thought sequences with branching and
  revision capabilities.
tags:
- Thinking
- Problem Solving
- Reasoning
- Planning
- Official
author: Anthropic
featured: true
install_command: claude mcp add sequential-thinking -- npx -y @modelcontextprotocol/server-sequential-thinking
connection_type: stdio
paid_api: false
---

The Sequential Thinking MCP server provides a structured approach to problem-solving by breaking down complex tasks into thought sequences. It supports branching, revision, and dynamic adjustment of thinking paths.

## Installation

```bash
npm install -g @modelcontextprotocol/server-sequential-thinking
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    }
  }
}
```

## Available Tools

### sequentialthinking
Process a thought in a sequence with full context tracking.

```typescript
sequentialthinking(params: ThinkingParams): ThinkingResult
```

**Parameters:**
- `thought` - Current thinking step content
- `thoughtNumber` - Position in sequence (1-based)
- `totalThoughts` - Estimated total thoughts needed
- `nextThoughtNeeded` - Whether more thinking is required
- `isRevision` - If revising a previous thought
- `revisesThought` - Which thought number is being revised
- `branchFromThought` - Branch point for alternative paths
- `branchId` - Identifier for the current branch
- `needsMoreThoughts` - Signal to extend the sequence

## Features

### Dynamic Adjustment
- Adjust total thoughts up or down as understanding deepens
- Add more thoughts even after reaching initial estimate

### Branching
- Create alternative thinking paths
- Explore multiple solutions simultaneously
- Compare different approaches

### Revision
- Revisit and revise previous thoughts
- Correct mistakes in reasoning
- Refine understanding iteratively

### Uncertainty Handling
- Express uncertainty explicitly
- Explore alternatives when unsure
- Build confidence through iteration

## Usage Example

```
Claude, use sequential thinking to break down the problem
of designing a caching system for our API, considering
different strategies and trade-offs.
```

## Best Practices

1. Start with an initial estimate but be ready to adjust
2. Express uncertainty when present
3. Use branching to explore alternatives
4. Mark revisions clearly
5. Continue until truly satisfied with the solution
