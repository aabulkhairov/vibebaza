---
title: AI Tasks MCP сервер
description: Система управления задачами с имплементацией Model Context Protocol (MCP)
  для бесшовной интеграции с агентными AI инструментами. Позволяет AI агентам создавать,
  управлять и отслеживать задачи в планах с использованием Valkey как слоя персистентности.
tags:
- Database
- Productivity
- AI
- Integration
- Analytics
author: jbrinkman
featured: false
---

Система управления задачами с имплементацией Model Context Protocol (MCP) для бесшовной интеграции с агентными AI инструментами. Позволяет AI агентам создавать, управлять и отслеживать задачи в планах с использованием Valkey как слоя персистентности.

## Установка

### Docker (SSE)

```bash
docker run -d --name valkey-mcp \
  -p 8080:8080 \
  -p 6379:6379 \
  -v valkey-data:/data \
  -e ENABLE_SSE=true \
  ghcr.io/jbrinkman/valkey-ai-tasks:latest
```

### Docker (Streamable HTTP)

```bash
docker run -d --name valkey-mcp \
  -p 8080:8080 \
  -p 6379:6379 \
  -v valkey-data:/data \
  -e ENABLE_STREAMABLE_HTTP=true \
  ghcr.io/jbrinkman/valkey-ai-tasks:latest
```

### Docker (STDIO)

```bash
docker run -i --rm --name valkey-mcp \
  -v valkey-data:/data \
  -e ENABLE_STDIO=true \
  ghcr.io/jbrinkman/valkey-ai-tasks:latest
```

### Docker Pull

```bash
docker pull ghcr.io/jbrinkman/valkey-ai-tasks:latest
```

### Создание Volume

```bash
docker volume create valkey-data
```

## Конфигурация

### SSE Transport

```json
{
  "mcpServers": {
    "valkey-tasks": {
      "serverUrl": "http://localhost:8080/sse"
    }
  }
}
```

### Streamable HTTP Transport

```json
{
  "mcpServers": {
    "valkey-tasks": {
      "serverUrl": "http://localhost:8080/mcp"
    }
  }
}
```

### STDIO Transport

```json
{
  "mcpServers": {
    "valkey-tasks": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-v", "valkey-data:/data"
        "-e", "ENABLE_STDIO=true",
        "ghcr.io/jbrinkman/valkey-ai-tasks:latest"
      ]
    }
  }
}
```

### Docker SSE Transport

```json
{
  "mcpServers": {
    "valkey-tasks": {
      "serverUrl": "http://valkey-mcp-server:8080/sse"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `create_plan` | Создать новый план |
| `get_plan` | Получить план по ID |
| `list_plans` | Список всех планов |
| `list_plans_by_application` | Список всех планов для конкретного приложения |
| `update_plan` | Обновить существующий план |
| `delete_plan` | Удалить план по ID |
| `update_plan_notes` | Обновить заметки плана |
| `get_plan_notes` | Получить заметки плана |
| `create_task` | Создать новую задачу в плане |
| `get_task` | Получить задачу по ID |
| `list_tasks_by_plan` | Список всех задач в плане |
| `list_tasks_by_status` | Список всех задач с определённым статусом |
| `update_task` | Обновить существующую задачу |
| `delete_task` | Удалить задачу по ID |
| `reorder_task` | Изменить порядок задачи в плане |

## Возможности

- Управление планами (создание, чтение, обновление, удаление)
- Управление задачами (создание, чтение, обновление, удаление)
- Упорядочивание и приоритизация задач
- Отслеживание статусов задач
- Поддержка заметок с Markdown форматированием для планов и задач
- MCP сервер для интеграции с AI агентами
- Поддержка STDIO, SSE и Streamable HTTP транспортных протоколов
- Docker контейнер для простого деплоя
- MCP ресурсы для эффективного доступа к данным
- Массовое создание задач за один раз

## Переменные окружения

### Опциональные
- `ENABLE_SSE` — включить Server-Sent Events транспорт
- `ENABLE_STREAMABLE_HTTP` — включить Streamable HTTP транспорт
- `ENABLE_STDIO` — включить STDIO транспорт для прямой коммуникации с процессом

## Примеры использования

```
I need to organize work for my new application called "inventory-manager". Create a plan for this application with plan notes about creating a comprehensive inventory management system, and add tasks for setting up database schema, implementing REST API endpoints, creating user authentication, designing frontend dashboard, and implementing inventory tracking features.
```

## Ресурсы

- [GitHub Repository](https://github.com/jbrinkman/valkey-ai-tasks)

## Примечания

Система предоставляет MCP ресурсы для эффективного доступа к данным с URI паттернами типа 'ai-tasks://plans/{id}/full' для полного просмотра планов. Функциональность заметок поддерживает полный Markdown: заголовки, списки, таблицы, блоки кода, ссылки и изображения. Сервер автоматически выбирает транспорт на основе URL path и content type.
