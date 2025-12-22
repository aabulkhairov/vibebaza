---
title: TickTick MCP сервер
description: MCP сервер, который интегрируется с TickTick API, обеспечивая комплексное управление задачами, организацию проектов, отслеживание привычек и автоматизацию с OAuth2 аутентификацией.
tags:
- Productivity
- API
- Integration
author: alexarevalo9
featured: false
---

MCP сервер, который интегрируется с TickTick API, обеспечивая комплексное управление задачами, организацию проектов, отслеживание привычек и автоматизацию с OAuth2 аутентификацией.

## Установка

### NPX

```bash
npx @alexarevalo.ai/mcp-server-ticktick
```

### Docker

```bash
docker build -t mcp/ticktick -f src/ticktick/Dockerfile .
docker run -i --rm -e TICKTICK_CLIENT_ID -e TICKTICK_CLIENT_SECRET -e TICKTICK_ACCESS_TOKEN mcp/ticktick
```

### Smithery

```bash
npx -y @smithery/cli install @alexarevalo9/ticktick-mcp-server --client claude
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "ticktick": {
      "command": "npx",
      "args": ["-y", "@alexarevalo.ai/mcp-server-ticktick"],
      "env": {
        "TICKTICK_CLIENT_ID": "<YOUR_CLIENT_ID>",
        "TICKTICK_CLIENT_SECRET": "<YOUR_CLIENT_SECRET>",
        "TICKTICK_ACCESS_TOKEN": "<YOUR_ACCESS_TOKEN>"
      }
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "ticktick": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "TICKTICK_CLIENT_ID",
        "-e",
        "TICKTICK_CLIENT_SECRET",
        "-e",
        "TICKTICK_ACCESS_TOKEN",
        "mcp/ticktick"
      ],
      "env": {
        "TICKTICK_CLIENT_ID": "<YOUR_CLIENT_ID>",
        "TICKTICK_CLIENT_SECRET": "<YOUR_CLIENT_SECRET>",
        "TICKTICK_ACCESS_TOKEN": "<YOUR_ACCESS_TOKEN>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_task_by_ids` | Получить конкретную задачу по ID проекта и ID задачи |
| `create_task` | Создать новую задачу в проекте с полными возможностями настройки |
| `update_task` | Обновить существующую задачу с любыми доступными свойствами |
| `complete_task` | Отметить задачу как выполненную |
| `delete_task` | Удалить задачу из проекта |
| `get_user_projects` | Получить все проекты аутентифицированного пользователя |
| `get_project_by_id` | Получить конкретный проект по ID |
| `get_project_with_data` | Получить детали проекта вместе с задачами и колонками |
| `create_project` | Создать новый проект с настраиваемыми режимами просмотра и параметрами |
| `update_project` | Обновить свойства существующего проекта |
| `delete_project` | Удалить проект |

## Возможности

- Управление задачами: создание, чтение, обновление и удаление задач со всеми доступными свойствами
- Управление проектами: создание, чтение, обновление и удаление проектов с настраиваемыми видами
- Поддержка подзадач: полная поддержка управления подзадачами внутри родительских задач
- Полное управление задачами: установка приоритетов, сроков выполнения, напоминаний и правил повторения
- OAuth аутентификация: полная реализация OAuth2 для безопасного доступа к API
- Комплексная обработка ошибок: понятные сообщения об ошибках для типичных проблем

## Переменные окружения

### Обязательные
- `TICKTICK_CLIENT_ID` - Client ID приложения TickTick из портала разработчика
- `TICKTICK_CLIENT_SECRET` - Client secret приложения TickTick из портала разработчика
- `TICKTICK_ACCESS_TOKEN` - OAuth токен доступа, созданный через процесс аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/alexarevalo9/ticktick-mcp-server)

## Примечания

Требует настройки OAuth аутентификации через TickTick Developer Portal. Токены доступа истекают через 180 дней. Поддерживает формат iCalendar для напоминаний и правил повторения. Включает комплексные свойства задач с уровнями приоритета (0-5), форматированием дат в ISO 8601 и несколькими режимами просмотра проектов (список, канбан, временная шкала).