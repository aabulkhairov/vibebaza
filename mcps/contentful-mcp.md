---
title: Contentful-mcp MCP сервер
description: MCP сервер, который интегрируется с Contentful's Content Management API, предоставляя комплексные возможности управления контентом, включая CRUD операции для записей, ресурсов, комментариев, пространств и типов контента.
tags:
- CRM
- API
- Productivity
- Storage
- Integration
author: Community
featured: false
---

MCP сервер, который интегрируется с Contentful's Content Management API, предоставляя комплексные возможности управления контентом, включая CRUD операции для записей, ресурсов, комментариев, пространств и типов контента.

## Установка

### NPX

```bash
npx -y @ivotoby/contentful-management-mcp-server
```

### Smithery

```bash
npx -y @smithery/cli install @ivotoby/contentful-management-mcp-server --client claude
```

## Конфигурация

### Claude Desktop (Переменные окружения)

```json
{
  "mcpServers": {
    "contentful": {
      "command": "npx",
      "args": ["-y", "@ivotoby/contentful-management-mcp-server"],
      "env": {
        "CONTENTFUL_MANAGEMENT_ACCESS_TOKEN": "<Your CMA token>"
      }
    }
  }
}
```

### Claude Desktop (Аргументы)

```json
{
  "mcpServers": {
    "contentful": {
      "command": "npx",
      "args": [
        "-y",
        "@ivotoby/contentful-management-mcp-server",
        "--management-token",
        "<your token>",
        "--host",
        "http://api.contentful.com"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_entries` | Поиск записей с использованием параметров запроса |
| `create_entry` | Создание новых записей |
| `get_entry` | Получение существующих записей |
| `update_entry` | Обновление полей записи |
| `delete_entry` | Удаление записей |
| `publish_entry` | Публикация записей |
| `unpublish_entry` | Снятие записей с публикации |
| `get_comments` | Получение комментариев для записи с фильтрацией по статусу |
| `create_comment` | Создание новых комментариев к записям с поддержкой вложенных обсуждений |
| `get_single_comment` | Получение конкретного комментария по его ID для записи |
| `delete_comment` | Удаление конкретного комментария из записи |
| `update_comment` | Обновление существующих комментариев с новым содержимым или изменением статуса |
| `bulk_publish` | Публикация множественных записей и ресурсов в одной операции |
| `bulk_unpublish` | Снятие с публикации множественных записей и ресурсов в одной операции |
| `bulk_validate` | Валидация множественных записей на предмет согласованности контента, ссылок и обязательных полей |

## Возможности

- Полные CRUD операции для записей и ресурсов
- Управление комментариями с поддержкой вложенных обсуждений
- Управление пространствами и окружениями
- Управление определениями типов контента
- Поддержка локализации для множественных локалей
- Контроль рабочего процесса публикации контента
- Массовые операции для публикации, снятия с публикации и валидации
- Умная пагинация (3 элемента на запрос для предотвращения переполнения контекста)
- Поддержка как stdio, так и StreamableHTTP режимов транспорта
- Поддержка аутентификации App Identity

## Переменные окружения

### Обязательные
- `CONTENTFUL_MANAGEMENT_ACCESS_TOKEN` - Ваш токен Content Management API

### Опциональные
- `CONTENTFUL_HOST` - Конечная точка Contentful Management API (по умолчанию https://api.contentful.com)
- `ENABLE_HTTP_SERVER` - Установите в 'true' для включения HTTP/SSE режима
- `HTTP_PORT` - Порт для HTTP сервера (по умолчанию: 3000)
- `HTTP_HOST` - Хост для HTTP сервера (по умолчанию: localhost)
- `SPACE_ID` - Ограничить операции конкретным ID пространства
- `ENVIRONMENT_ID` - Ограничить операции конкретным ID окружения

## Ресурсы

- [GitHub Repository](https://github.com/ivo-toby/contentful-mcp)

## Примечания

Это сообщественный сервер с официальным сервером Contentful, также доступным отдельно. Поддерживает как токены Management API, так и аутентификацию App Identity. Включает MCP Inspector для разработки и отладки. Внимание: Этот сервер предоставляет полные возможности управления контентом, включая удаление, поэтому используйте с осторожностью. Официально не поддерживается Contentful.