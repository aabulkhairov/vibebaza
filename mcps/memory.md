---
title: Memory MCP
description: Knowledge graph-based persistent memory system that lets Claude remember
  information across conversations.
tags:
- Memory
- Knowledge Graph
- Persistence
- Official
author: Anthropic
featured: true
install_command: claude mcp add memory -- npx -y @modelcontextprotocol/server-memory
connection_type: stdio
paid_api: true
---

The Memory MCP server provides Claude with persistent memory using a local knowledge graph. This lets Claude remember information about users across chats through entities, relations, and observations.

## Installation

```bash
npm install -g @modelcontextprotocol/server-memory
```

## Configuration

Add to your Claude Code settings:

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-memory"
      ]
    }
  }
}
```

### Custom Memory File Path

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"],
      "env": {
        "MEMORY_FILE_PATH": "/path/to/custom/memory.jsonl"
      }
    }
  }
}
```

## Core Concepts

### Entities
Primary nodes in the knowledge graph with a unique name, type, and observations.

```json
{
  "name": "John_Smith",
  "entityType": "person",
  "observations": ["Speaks fluent Spanish"]
}
```

### Relations
Directed connections between entities in active voice.

```json
{
  "from": "John_Smith",
  "to": "Anthropic",
  "relationType": "works_at"
}
```

### Observations
Discrete, atomic pieces of information attached to entities.

## Available Tools

### create_entities
Create multiple new entities in the knowledge graph.

```typescript
create_entities(entities: Entity[]): void
```

### create_relations
Create relations between entities.

```typescript
create_relations(relations: Relation[]): void
```

### add_observations
Add new observations to existing entities.

```typescript
add_observations(observations: ObservationInput[]): AddedObservations[]
```

### delete_entities
Remove entities and their associated relations.

```typescript
delete_entities(entityNames: string[]): void
```

### delete_observations
Remove specific observations from entities.

```typescript
delete_observations(deletions: DeletionInput[]): void
```

### delete_relations
Remove specific relations from the graph.

```typescript
delete_relations(relations: Relation[]): void
```

### read_graph
Read the entire knowledge graph.

```typescript
read_graph(): KnowledgeGraph
```

### search_nodes
Search for nodes by query across names, types, and observations.

```typescript
search_nodes(query: string): SearchResults
```

### open_nodes
Retrieve specific nodes by name with their relations.

```typescript
open_nodes(names: string[]): NodeResults
```

## Recommended System Prompt

Add this to your Claude project for optimal memory usage:

```
Follow these steps for each interaction:

1. User Identification:
   - Assume you are interacting with default_user
   - Proactively try to identify the user if unknown

2. Memory Retrieval:
   - Begin chats by saying "Remembering..." and retrieve relevant information
   - Refer to the knowledge graph as your "memory"

3. Memory Updates:
   - Be attentive to new information: identity, behaviors, preferences, goals, relationships
   - Create entities for recurring people, organizations, and events
   - Connect them using relations and store facts as observations
```

## Usage Example

```
Claude, remember that I prefer morning meetings and
my favorite programming language is Python.
```
