---
title: Roundtable MCP сервер
description: Локальный MCP сервер, который координирует специализированных AI суб-агентов (Gemini, Claude, Codex, Cursor) для решения сложных инженерных задач параллельно с общим контекстом между всеми моделями.
tags:
- AI
- Code
- Productivity
- Integration
- Analytics
author: askbudi
featured: false
install_command: claude mcp add roundtable-ai -- roundtable-ai --agents gemini,claude,codex,cursor
---

Локальный MCP сервер, который координирует специализированных AI суб-агентов (Gemini, Claude, Codex, Cursor) для решения сложных инженерных задач параллельно с общим контекстом между всеми моделями.

## Установка

### pip

```bash
pip install roundtable-ai
```

### UVX

```bash
uvx roundtable-ai@latest
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "roundtable-ai": {
      "command": "roundtable-ai",
      "env": {
        "CLI_MCP_SUBAGENTS": "codex,claude,cursor,gemini"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "roundtable-ai": {
      "type": "stdio",
      "command": "uvx",
      "args": [
        "roundtable-ai@latest"
      ],
      "env": {
        "CLI_MCP_SUBAGENTS": "codex,claude,cursor,gemini"
      }
    }
  }
}
```

### VS Code

```json
{
  "mcp.servers": {
    "roundtable-ai": {
      "command": "roundtable-ai",
      "env": {
        "CLI_MCP_SUBAGENTS": "codex,claude,cursor,gemini"
      }
    }
  }
}
```

## Возможности

- Непрерывность контекста: Общий контекст проекта для всех суб-агентов
- Параллельное выполнение: Все агенты работают одновременно
- Специализация моделей: Правильный AI для каждой задачи (контекст 1М у Gemini, рассуждения Claude, реализация Codex)
- Без наценок: Использует ваши существующие CLI инструменты и подписки API
- Поддержка 26+ IDE: Работает с Claude Code, Cursor, VS Code, JetBrains и другими

## Переменные окружения

### Опциональные
- `CLI_MCP_SUBAGENTS` - Список суб-агентов через запятую для активации (codex,claude,cursor,gemini)

## Примеры использования

```
The user dashboard is randomly slow for enterprise customers. Use Gemini SubAgent to analyze frontend performance issues in the React components, especially expensive re-renders and inefficient data fetching. Use Codex SubAgent to examine the backend API endpoint for N+1 queries and database bottlenecks. Use Claude SubAgent to review the infrastructure logs and identify memory/CPU pressure during peak hours.
```

```
I'm debugging a critical production issue. The user sees a "Failed to load data" message. Use Gemini SubAgent to analyze the logs from both stacks, correlate the events, and form a hypothesis about the root cause. Use Codex SubAgent to analyze the Python backend traceback and suggest a specific code fix for the database connection error.
```

```
Our checkout API p95 latency increased from 220ms to 780ms. Need optimization strategy. Use Claude SubAgent to analyze the EXPLAIN plan and identify why the query is slow. Use Codex SubAgent to rewrite the SQL with proper JOINs and suggest indexes. Use Gemini SubAgent to fix the N+1 query problem with batch fetching.
```

## Ресурсы

- [GitHub Repository](https://github.com/askbudi/roundtable)

## Примечания

Поддерживает установку в один клик для Cursor через deeplink. Можно запускать только с определенными агентами, используя флаг --agents. Использует существующие API ключи и подписки без наценок.