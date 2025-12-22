---
title: Agent Interviews MCP сервер
description: Доступ к данным Agent Interviews напрямую из Claude и Cursor через Model
  Context Protocol (MCP). Agent Interviews — это AI-платформа интервью как сервис для
  технических оценок.
tags:
- AI
- API
- Analytics
- Productivity
author: thinkchainai
featured: false
---

Доступ к данным Agent Interviews напрямую из Claude и Cursor через Model Context Protocol (MCP). Agent Interviews — это AI-платформа интервью как сервис для технических оценок.

## Установка

### NPX Remote

```bash
npx -y mcp-remote@latest https://api.agentinterviews.com/mcp --header "Authorization:${API_KEY}"
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "AgentInterviews": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote@latest",
        "https://api.agentinterviews.com/mcp",
        "--header",
        "Authorization:${API_KEY}"
      ],
      "env": {
        "API_KEY": "Api-Key YOUR_API_KEY_HERE"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "agentinterviews": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote@latest",
        "https://api.agentinterviews.com/mcp",
        "--header",
        "Authorization:${API_KEY}"
      ],
      "env": {
        "API_KEY": "Api-Key YOUR_API_KEY_HERE"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `agentinterviews_list_projects` | Список всех проектов |
| `agentinterviews_get_interview` | Детали конкретного интервью |
| `agentinterviews_list_interviewers` | Список всех интервьюеров |
| `agentinterviews_get_transcript` | Получить транскрипт интервью |

## Возможности

- Безопасный API доступ: подключение к аккаунту Agent Interviews через API ключ
- Префиксованные инструменты: все инструменты используют префикс agentinterviews_ для избежания коллизий с другими MCP
- Комплексная функциональность: доступ к интервью, транскриптам, отчётам, проектам и многому другому
- Интуитивные запросы: задавай вопросы на естественном языке, AI сам определит нужные инструменты

## Переменные окружения

### Обязательные
- `API_KEY` — API ключ Agent Interviews для аутентификации (формат: 'Api-Key YOUR_API_KEY_HERE')

## Примеры использования

```
Show me the status of my recent interviews
```

```
Get the transcript from my last interview with candidate John Smith
```

```
What projects do I have available?
```

```
Show me details about the 'Senior Developer' interviewer
```

## Ресурсы

- [GitHub Repository](https://github.com/thinkchainai/agentinterviews_mcp)

## Примечания

Требуется аккаунт Agent Interviews с API доступом. Сервер использует удалённое MCP подключение к https://api.agentinterviews.com/mcp. Никогда не делись API ключом и не включай его в публичные репозитории.
