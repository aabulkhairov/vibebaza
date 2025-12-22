---
title: ClickUp MCP сервер
description: Model Context Protocol (MCP) сервер для интеграции задач ClickUp с AI приложениями, позволяющий AI агентам взаимодействовать с задачами ClickUp, пространствами, списками, папками, отслеживанием времени и документами через стандартизированный протокол.
tags:
- Productivity
- API
- Integration
- CRM
- Analytics
author: Community
featured: false
---

Model Context Protocol (MCP) сервер для интеграции задач ClickUp с AI приложениями, позволяющий AI агентам взаимодействовать с задачами ClickUp, пространствами, списками, папками, отслеживанием времени и документами через стандартизированный протокол.

## Установка

### Smithery (Хостинг)

```bash
Available on Smithery at https://smithery.ai/server/@taazkareem/clickup-mcp-server
```

### NPX

```bash
npx -y @taazkareem/clickup-mcp-server@latest --env CLICKUP_API_KEY=your-api-key --env CLICKUP_TEAM_ID=your-team-id
```

## Конфигурация

### Claude Desktop Базовая

```json
{
  "mcpServers": {
    "ClickUp": {
      "command": "npx",
      "args": [
        "-y",
        "@taazkareem/clickup-mcp-server@latest"
      ],
      "env": {
        "CLICKUP_API_KEY": "your-api-key",
        "CLICKUP_TEAM_ID": "your-team-id",
        "DOCUMENT_SUPPORT": "true"
      }
    }
  }
}
```

### Поддержка HTTP транспорта

```json
{
  "mcpServers": {
    "ClickUp": {
      "command": "npx",
      "args": [
        "-y",
        "@taazkareem/clickup-mcp-server@latest"
      ],
      "env": {
        "CLICKUP_API_KEY": "your-api-key",
        "CLICKUP_TEAM_ID": "your-team-id",
        "ENABLE_SSE": "true",
        "PORT": "3231"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_workspace_hierarchy` | Получить структуру рабочего пространства |
| `create_task` | Создать задачу |
| `create_bulk_tasks` | Создать несколько задач |
| `update_task` | Изменить задачу |
| `update_bulk_tasks` | Обновить несколько задач |
| `get_tasks` | Получить задачи из списка |
| `get_task` | Получить детали одной задачи |
| `get_workspace_tasks` | Получить задачи с фильтрацией |
| `get_task_comments` | Получить комментарии к задаче |
| `create_task_comment` | Добавить комментарий к задаче |
| `attach_task_file` | Прикрепить файл к задаче |

## Возможности

- Создавать, обновлять и удалять задачи с одиночными и массовыми операциями
- Перемещать и дублировать задачи в любом месте рабочего пространства
- Устанавливать даты начала/завершения с помощью естественного языка
- Создавать и управлять подзадачами, комментариями и вложениями
- Отслеживание времени с функциями старт/стоп и ручным вводом
- Управление тегами с командами цвета на естественном языке
- Управление документами с созданием, листингом и обновлениями
- Управление участниками с поиском по имени/email и назначением задач
- Организация рабочего пространства с навигацией по пространствам, папкам и спискам
- HTTP Streamable транспорт и поддержка legacy SSE

## Переменные окружения

### Обязательные
- `CLICKUP_API_KEY` - ключ API ClickUp для аутентификации
- `CLICKUP_TEAM_ID` - ID команды из URL вашего рабочего пространства ClickUp

### Опциональные
- `DOCUMENT_SUPPORT` - включить функциональность поддержки документов
- `ENABLED_TOOLS` - список инструментов через запятую для включения (имеет приоритет)
- `DISABLED_TOOLS` - список инструментов через запятую для отключения
- `ENABLE_SSE` - включить HTTP/SSE транспорт
- `PORT` - порт для HTTP сервера
- `ENABLE_STDIO` - включить STDIO транспорт
- `ENABLE_SECURITY_FEATURES` - включить заголовки безопасности и логирование
- `ENABLE_HTTPS` - включить HTTPS/TLS шифрование

## Ресурсы

- [GitHub Repository](https://github.com/TaazKareem/clickup-mcp-server)

## Примечания

Сервер поддерживает 36 инструментов в общей сложности и включает всестороннюю интеграцию с ClickUp. Официальный ClickUp MCP сервер был выпущен на основе этого репозитория. Сервер поддерживает как HTTP Streamable транспорт (совместимый с MCP Inspector), так и legacy SSE транспорт для обратной совместимости. Функции безопасности включаются по желанию и по умолчанию отключены. Рекомендуется фильтрация инструментов при возникновении проблем с ограничениями контекста.