---
title: Quickchat AI MCP сервер
description: MCP сервер, который позволяет пользователям интегрировать своих агентов Quickchat AI в AI-приложения, такие как Claude Desktop, Cursor и VS Code, предоставляя доступ к Knowledge Base агента и возможностям для диалогов.
tags:
- AI
- Integration
- API
- Productivity
- Messaging
author: quickchatai
featured: false
---

MCP сервер, который позволяет пользователям интегрировать своих агентов Quickchat AI в AI-приложения, такие как Claude Desktop, Cursor и VS Code, предоставляя доступ к Knowledge Base агента и возможностям для диалогов.

## Установка

### UV Package Manager

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### PyPI Package

```bash
uvx quickchat-ai-mcp
```

### Из исходников

```bash
uv run mcp dev src/__main__.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "< QUICKCHAT AI MCP NAME >": {
      "command": "uvx",
      "args": ["quickchat-ai-mcp"],
      "env": {
        "SCENARIO_ID": "< QUICKCHAT AI SCENARIO ID >",
        "API_KEY": "< QUICKCHAT AI API KEY >"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "< QUICKCHAT AI MCP NAME >": {
      "command": "uvx",
      "args": ["quickchat-ai-mcp"],
      "env": {
        "SCENARIO_ID": "< QUICKCHAT AI SCENARIO ID >",
        "API_KEY": "< QUICKCHAT AI API KEY >"
      }
    }
  }
}
```

### Отладка из исходников

```json
{
  "mcpServers": {
    "< QUICKCHAT AI MCP NAME >": {
      "command": "uv",
      "args": [
        "run",
        "--with",
        "mcp[cli]",
        "--with",
        "requests",
        "mcp",
        "run",
        "< YOUR PATH>/quickchat-ai-mcp/src/__main__.py"
      ],
      "env": {
        "SCENARIO_ID": "< QUICKCHAT AI SCENARIO ID >",
        "API_KEY": "< QUICKCHAT AI API KEY >"
      }
    }
  }
}
```

### Публичный деплой (без API ключа)

```json
{
  "mcpServers": {
    "< QUICKCHAT AI MCP NAME >": {
      "command": "uvx",
      "args": ["quickchat-ai-mcp"],
      "env": {
        "SCENARIO_ID": "< QUICKCHAT AI SCENARIO ID >"
      }
    }
  }
}
```

## Возможности

- Управление всеми аспектами вашего MCP из дашборда Quickchat AI с деплоем в одно нажатие
- Просмотр всех диалогов в Quickchat Inbox, показывающий взаимодействия AI-с-AI
- Открытые сообщения к агентам Quickchat AI вместо статичной реализации инструментов
- Доступ к Knowledge Base и возможностям для диалогов в реальном времени
- Поддержка множества AI-приложений (Claude Desktop, Cursor, VS Code, Windsurf)
- Опциональное требование API ключа для публичного деплоя

## Переменные окружения

### Обязательные
- `SCENARIO_ID` - Идентификатор сценария Quickchat AI

### Опциональные
- `API_KEY` - API ключ Quickchat AI (опционально для публичного деплоя)

## Ресурсы

- [GitHub Repository](https://github.com/incentivai/quickchat-ai-mcp)

## Примечания

Требуется аккаунт Quickchat AI с 7-дневным триалом. Пользователи должны настроить Knowledge Base своего AI, возможности и настройки в приложении Quickchat AI. Название MCP, описание и команда настраиваются через дашборд Quickchat AI и важны для понимания AI-приложениями, когда обращаться к вашему AI. Для публичного деплоя отключите переключатель 'Require API key' и поделитесь конфигурацией без API ключа.