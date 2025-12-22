---
title: GitHub Projects MCP сервер
description: Model Context Protocol (MCP) сервер, который предоставляет инструменты для работы с GitHub Projects через GraphQL, обеспечивая полное управление проектами, включая элементы, поля и рабочие процессы.
tags:
- DevOps
- Code
- Productivity
- API
- Integration
author: redducklabs
featured: false
install_command: claude mcp add github-projects github-projects-mcp -e GITHUB_TOKEN=your_token_here
---

Model Context Protocol (MCP) сервер, который предоставляет инструменты для работы с GitHub Projects через GraphQL, обеспечивая полное управление проектами, включая элементы, поля и рабочие процессы.

## Установка

### Из исходного кода

```bash
git clone https://github.com/redducklabs/github-projects-mcp.git
cd github-projects-mcp
pip install -e .
```

### Используя pip

```bash
pip install github-projects-mcp
```

### Используя uv

```bash
uv add github-projects-mcp
```

### DXT Package

```bash
Download the .dxt file from releases and install in Claude Desktop
```

## Конфигурация

### Claude Code (PyPI)

```json
claude mcp add github-projects github-projects-mcp -e GITHUB_TOKEN=your_token_here
```

### Claude Code (Source)

```json
claude mcp add github-projects ./venv/Scripts/python github_projects_mcp/server.py -e GITHUB_TOKEN=your_token_here -e PYTHONPATH=/full/path/to/github-projects-mcp
```

### Claude Desktop Manual

```json
{
  "mcpServers": {
    "github-projects": {
      "command": "github-projects-mcp",
      "env": {
        "GITHUB_TOKEN": "your_github_token_here"
      }
    }
  }
}
```

### VS Code MCP

```json
{
  "inputs": [
    {
      "type": "promptString",
      "id": "github-token",
      "description": "GitHub Personal Access Token",
      "password": true
    }
  ],
  "servers": {
    "github-projects": {
      "type": "stdio",
      "command": "github-projects-mcp",
      "env": {
        "GITHUB_TOKEN": "${input:github-token}"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `list_accessible_projects` | Получить список всех проектов, доступных аутентифицированному пользователю |
| `get_organization_projects` | Получить проекты организации |
| `get_user_projects` | Получить проекты пользователя |
| `get_project` | Получить конкретный проект по ID |
| `create_project` | Создать новый проект |
| `update_project` | Обновить детали проекта |
| `delete_project` | Удалить проект |
| `get_project_items` | Получить элементы проекта (полные данные) |
| `get_project_items_advanced` | Получить элементы с кастомным выбором GraphQL полей для эффективности |
| `add_item_to_project` | Добавить элемент в проект |
| `update_item_field_value` | Обновить значения полей элемента |
| `remove_item_from_project` | Удалить элемент из проекта |
| `archive_item` | Архивировать элемент проекта |
| `get_project_fields` | Получить поля проекта |
| `search_project_items` | Искать элементы по содержимому/полям |

## Возможности

- Полное покрытие GitHub Projects API со всеми основными операциями
- Множественные транспортные режимы (stdio, SSE, HTTP streaming)
- Надежная обработка ошибок с отображением ошибок GitHub API
- Настраиваемые повторы при достижении лимита запросов
- Типовая безопасность с моделями Pydantic
- Конфигурация через переменные окружения
- Обнаружение и управление проектами
- Управление элементами проектов (добавление, обновление, удаление, архивирование)
- Работа с полями проектов
- Возможности поиска и фильтрации

## Переменные окружения

### Обязательные
- `GITHUB_TOKEN` - GitHub Personal Access Token с областями project и read:project

### Опциональные
- `API_MAX_RETRIES` - Максимальное количество повторов при ограничении скорости запросов (по умолчанию: 3)
- `API_RETRY_DELAY` - Задержка в секундах между повторами (по умолчанию: 60)
- `MCP_TRANSPORT` - Транспортный режим - stdio, sse, или http (по умолчанию: stdio)
- `MCP_HOST` - Хост для SSE/HTTP режимов (по умолчанию: localhost)
- `MCP_PORT` - Порт для SSE/HTTP режимов (по умолчанию: 8000)
- `LOG_LEVEL` - Уровень логирования - DEBUG, INFO, WARNING, ERROR (по умолчанию: INFO)

## Примеры использования

```
@github-projects show me all projects for my organization 'mycompany'
```

```
@github-projects add issue #123 from repo mycompany/myproject to project PVT_kwDOABCDEF
```

```
@github-projects update the status field for item PVTI_lADOGHIJKL to 'In Progress'
```

```
@github-projects create a new project called 'Q1 Planning' for organization mycompany
```

```
@github-projects help me manage my project
```

## Ресурсы

- [GitHub Repository](https://github.com/redducklabs/github-projects-mcp)

## Примечания

Требует GitHub Personal Access Token с областями 'project' и 'read:project'. Для проектов организации используйте Fine-grained Personal Access Token с доступом к ресурсам организации. Поддерживает транспортные режимы stdio (по умолчанию), SSE и HTTP. Совместим с Claude Code, VS Code MCP и Claude Desktop.