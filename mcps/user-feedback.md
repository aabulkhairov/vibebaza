---
title: User Feedback MCP сервер
description: Простой MCP сервер для организации интерактивного рабочего процесса с участием человека в инструментах типа Cline и Cursor. Особенно полезен при разработке десктопных приложений, требующих сложного пользовательского взаимодействия для тестирования.
tags:
- Productivity
- DevOps
- Integration
- Code
author: Community
featured: false
---

Простой MCP сервер для организации интерактивного рабочего процесса с участием человека в инструментах типа Cline и Cursor. Особенно полезен при разработке десктопных приложений, требующих сложного пользовательского взаимодействия для тестирования.

## Установка

### UV (Python)

```bash
pip install uv
# or
curl -LsSf https://astral.sh/uv/install.sh | sh
# Then clone repository and configure
```

### Разработка

```bash
uv run fastmcp dev server.py
```

## Конфигурация

### Cline

```json
{
  "mcpServers": {
    "github.com/mrexodia/user-feedback-mcp": {
      "command": "uv",
      "args": [
        "--directory",
        "c:\\MCP\\user-feedback-mcp",
        "run",
        "server.py"
      ],
      "timeout": 600,
      "autoApprove": [
        "user_feedback"
      ]
    }
  }
}
```

### Конфигурация проекта

```json
{
  "command": "npm run dev",
  "execute_automatically": false
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `user_feedback` | Запрашивает обратную связь от пользователей с параметрами директории проекта и сводки |

## Возможности

- Интеграция интерактивного рабочего процесса с участием человека
- Пользовательский интерфейс для обратной связи
- Конфигурация автоматического выполнения команд
- Специфичная для проекта конфигурация через .user-feedback.json
- Поддержка многошаговых команд с интеграцией Task
- Возможность автоматического одобрения для бесшовного рабочего процесса

## Примеры использования

```
Before completing the task, use the user_feedback MCP tool to ask the user for feedback.
```

## Ресурсы

- [GitHub Repository](https://github.com/mrexodia/user-feedback-mcp)

## Примечания

Создает файл .user-feedback.json в директории проекта для конфигурации. Если включен execute_automatically, команды будут выполняться мгновенно без ручного вмешательства. Веб-интерфейс доступен по адресу http://localhost:5173 во время разработки.