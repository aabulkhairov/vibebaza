---
title: LunarCrush Remote MCP сервер
description: Предоставляет актуальные социальные метрики и посты как для текущего живого социального контекста, так и для исторических метрик в оптимизированном для LLM и токенов виде, идеально подходит для автоматической торговли и финансового консультирования.
tags:
- Finance
- Analytics
- API
- AI
author: Community
featured: false
---

Предоставляет актуальные социальные метрики и посты как для текущего живого социального контекста, так и для исторических метрик в оптимизированном для LLM и токенов виде, идеально подходит для автоматической торговли и финансового консультирования.

## Конфигурация

### Remote HTTP Streamable

```json
{
  "mcpServers": {
    "LunarCrush": {
      "type": "http",
      "url": "https://lunarcrush.ai/mcp",
      "headers": {
        "Authorization": "Bearer ${input:lunarcrush-api-key}"
      }
    }
  }
}
```

### Remote SSE

```json
{
  "mcpServers": {
    "LunarCrush": {
      "type": "http",
      "url": "https://lunarcrush.ai/sse",
      "headers": {
        "Authorization": "Bearer ${input:lunarcrush-api-key}"
      }
    }
  }
}
```

### Local stdio

```json
{
  "mcpServers": {
    "LunarCrush": {
      "command": "node",
      "args": ["<absolute_path_to_project_root>/index.js"],
      "env": {
        "LUNARCRUSH_API_KEY": "<your_lunarcrush_api_key>"
      }
    }
  }
}
```

## Возможности

- Получение актуальных социальных метрик и постов
- Доступ как к текущему живому социальному контексту, так и к историческим метрикам
- Оптимизированные для LLM и токенов выходные данные
- Поддержка автоматической торговли и финансового консультирования

## Переменные окружения

### Обязательные
- `LUNARCRUSH_API_KEY` - API ключ для аутентификации LunarCrush

## Ресурсы

- [GitHub Repository](https://github.com/lunarcrush/mcp-server)

## Примечания

API ключи можно получить на https://lunarcrush.com/developers/api/authentication. Больше информации об использовании LunarCrush AI и возможностей MCP доступно на https://lunarcrush.com/developers/api/ai. Remote HTTP сервер является предпочтительным методом.