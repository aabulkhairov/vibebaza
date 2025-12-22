---
title: Snowflake Cortex MCP сервер
description: Предоставляет доступ к возможностям Snowflake Cortex AI, включая Cortex Search для неструктурированных данных, Cortex Analyst для запросов к структурированным данным и Cortex Agent для агентной оркестрации различных типов данных.
tags:
- Database
- AI
- Analytics
- Search
- Cloud
author: Community
featured: false
---

Предоставляет доступ к возможностям Snowflake Cortex AI, включая Cortex Search для неструктурированных данных, Cortex Analyst для запросов к структурированным данным и Cortex Agent для агентной оркестрации различных типов данных.

## Установка

### Yarn Dev

```bash
yarn dev
```

### MCP Inspector

```bash
yarn inspector
```

### MCP Inspector (NPX)

```bash
npx @modelcontextprotocol/inspector tsx --env-file .env dist/mcp/MCP.js
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Cortex Agent AI": {
      "command": "ABSOLUTE_PATH\\npx.cmd",
      "args": [
        "tsx",
        "--watch",
        "--env-file",
        "ABSOLUTE_PATH\\.env",
        "ABSOLUTE_PATH\\src\\mcp\\MCP.ts"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `cortex_search` | Запросы к неструктурированным данным в Snowflake для приложений Retrieval Augmented Generation (RAG) |
| `cortex_analyst_text_to_sql` | Запросы к структурированным данным в Snowflake через расширенное семантическое моделирование |
| `cortex_agent` | Агентный оркестратор для извлечения структурированных и неструктурированных данных |
| `sql_execution_tool` | Выполнение SQL запросов |

## Возможности

- Cortex Search для запросов к неструктурированным данным в RAG приложениях
- Cortex Analyst для запросов к структурированным данным через семантическое моделирование
- Cortex Agent для агентной оркестрации различных типов данных
- Payload Builder для динамического построения агентных запросов
- Поддержка потоковых ответов через SSE
- Поддержка нескольких инстансов Cortex Search и Analyst
- Конфигурация через переменные окружения

## Переменные окружения

### Обязательные
- `SNOWFLAKE_PAT` - Токен программного доступа для аутентификации в Snowflake

### Опциональные
- `SEMANTIC_MODEL_VIEW` - Файл семантической модели для инструмента Text2SQL
- `VEHICLES_SEARCH_SERVICE` - Название поискового сервиса транспортных средств

## Примеры использования

```
Show me the top selling brands by total sales quantity in TX for Books in 2003
```

## Ресурсы

- [GitHub Repository](https://github.com/thisisbhanuj/Snowflake-Cortex-MCP-Server)

## Примечания

MCP серверы работают как сопутствующие сервисы и взаимодействуют через stdio/sockets, а не HTTP. Их не следует путать с Next.js API бэкендами. Сервер использует Snowflake Cortex REST API для аутентификации и поддерживает множество MCP клиентов, включая Claude Desktop, VS Code с GitHub Copilot и другие. Токены программного доступа не оценивают вторичные роли и требуют правильной конфигурации ролей.