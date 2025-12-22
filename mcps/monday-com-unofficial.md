---
title: Monday.com (unofficial) MCP сервер
description: MCP сервер для monday.com, который позволяет MCP клиентам взаимодействовать с досками, элементами, обновлениями и документами Monday.com.
tags:
- Productivity
- CRM
- API
- Integration
author: Community
featured: false
---

MCP сервер для monday.com, который позволяет MCP клиентам взаимодействовать с досками, элементами, обновлениями и документами Monday.com.

## Установка

### uvx

```bash
uvx mcp-server-monday
```

### Docker

```bash
docker run --rm -i -e MONDAY_API_KEY=your-monday-api-key -e MONDAY_WORKSPACE_NAME=your-monday-workspace-name sakce/mcp-server-monday
```

### Из исходного кода

```bash
uv sync
uv build
```

### MCP Inspector (отладка)

```bash
npx @modelcontextprotocol/inspector uv run mcp-server-monday
```

## Конфигурация

### Claude Desktop (uvx)

```json
{
  "mcpServers": {
    "monday": {
      "command": "uvx",
      "args": [
        "mcp-server-monday"
      ],
      "env": {
        "MONDAY_API_KEY": "your-monday-api-key",
        "MONDAY_WORKSPACE_NAME": "your-monday-workspace-name"
      }
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "monday-docker": {
      "command": "docker",
      "args": [
        "run", 
        "--rm", 
        "-i", 
        "-e",
        "MONDAY_API_KEY=your-monday-api-key",
        "-e",
        "MONDAY_WORKSPACE_NAME=your-monday-workspace-name",
        "sakce/mcp-server-monday"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `monday-create-item` | Создаёт новый элемент или под-элемент на доске Monday.com |
| `monday-get-board-groups` | Получает все группы из указанной доски Monday.com |
| `monday-create-update` | Создаёт комментарий/обновление к элементу Monday.com |
| `monday-list-boards` | Выводит все доступные доски Monday.com |
| `monday-list-items-in-groups` | Выводит все элементы в указанных группах доски Monday.com |
| `monday-list-subitems-in-items` | Выводит все под-элементы для заданных элементов Monday.com |
| `monday-create-board` | Создаёт новую доску Monday.com |
| `monday-create-board-group` | Создаёт новую группу на доске Monday.com |
| `monday-move-item-to-group` | Перемещает элемент Monday.com в другую группу |
| `monday-delete-item` | Удаляет элемент Monday.com |
| `monday-archive-item` | Архивирует элемент Monday.com |
| `monday-get-item-updates` | Получает обновления/комментарии для конкретного элемента |
| `monday-get-docs` | Выводит документы в Monday.com с возможностью фильтрации по папке |
| `monday-get-doc-content` | Получает содержимое определённого документа |
| `monday-create-doc` | Создаёт новый документ в Monday.com |

## Возможности

- Создание и управление досками и группами досок Monday.com
- Создание, обновление, перемещение, удаление и архивирование элементов и под-элементов
- Публикация комментариев и обновлений к элементам
- Получение обновлений и комментариев элементов
- Управление документами и блоками документов Monday.com
- Просмотр и фильтрация досок, групп, элементов и документов

## Переменные окружения

### Обязательные
- `MONDAY_API_KEY` - Персональный API токен от Monday.com для аутентификации
- `MONDAY_WORKSPACE_NAME` - Название рабочего пространства из URL рабочего пространства Monday.com

## Примеры использования

```
Создание элементов на досках Monday.com
```

```
Публикация обновлений к существующим элементам
```

```
Перемещение элементов между группами
```

```
Выполнение действий в Monday.com, таких как создание элементов, публикация обновлений, перемещение элементов
```

## Ресурсы

- [GitHub Repository](https://github.com/sakce/mcp-server-monday)

## Примечания

Требует персональный API токен Monday.com и название рабочего пространства. Доступен через Rube.app для простой интеграции с клиентами вроде Cursor, Claude, VS Code и Windsurf. Файлы конфигурации расположены по адресу ~/Library/Application Support/Claude/claude_desktop_config.json на MacOS и %APPDATA%/Claude/claude_desktop_config.json на Windows.