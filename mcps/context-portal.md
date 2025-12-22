---
title: context-portal MCP сервер
description: MCP сервер с базой данных, который создает проектно-ориентированный граф знаний для AI-ассистентов, сохраняя решения, прогресс и архитектуру с векторными эмбеддингами для семантического поиска и RAG возможностей.
tags:
- Database
- Vector Database
- AI
- Storage
- Productivity
author: Community
featured: false
---

MCP сервер с базой данных, который создает проектно-ориентированный граф знаний для AI-ассистентов, сохраняя решения, прогресс и архитектуру с векторными эмбеддингами для семантического поиска и RAG возможностей.

## Установка

### UVX (Рекомендуется)

```bash
uvx --from context-portal-mcp conport-mcp --mode stdio --workspace_id ${workspaceFolder}
```

### Из исходников

```bash
git clone https://github.com/GreatScottyMac/context-portal.git
cd context-portal
uv venv
uv pip install -r requirements.txt
```

### Режим разработки

```bash
uv run --python .venv/bin/python --directory <path to context-portal repo> conport-mcp --mode stdio
```

## Конфигурация

### Конфигурация UVX (Рекомендуется)

```json
{
  "mcpServers": {
    "conport": {
      "command": "uvx",
      "args": [
        "--from",
        "context-portal-mcp",
        "conport-mcp",
        "--mode",
        "stdio",
        "--workspace_id",
        "${workspaceFolder}",
        "--log-file",
        "./logs/conport.log",
        "--log-level",
        "INFO"
      ]
    }
  }
}
```

### Без workspace ID при запуске

```json
{
  "mcpServers": {
    "conport": {
      "command": "uvx",
      "args": [
        "--from",
        "context-portal-mcp",
        "conport-mcp",
        "--mode",
        "stdio",
        "--log-file",
        "./logs/conport.log",
        "--log-level",
        "INFO"
      ]
    }
  }
}
```

### Конфигурация для разработки

```json
{
  "mcpServers": {
    "conport": {
      "command": "uv",
      "args": [
        "run",
        "--python",
        ".venv/bin/python",
        "--directory",
        "<path to context-portal repo> ",
        "conport-mcp",
        "--mode",
        "stdio",
        "--log-file",
        "./logs/conport-dev.log",
        "--log-level",
        "DEBUG"
      ],
      "disabled": false
    }
  }
}
```

## Возможности

- Структурированное хранение контекста с использованием SQLite (одна база данных на рабочее пространство)
- Поддержка нескольких рабочих пространств через workspace_id
- Хранение векторных данных и возможности семантического поиска
- Backend для Retrieval Augmented Generation (RAG)
- Граф знаний проекта с явными связями
- Эволюция схемы базы данных с использованием миграций Alembic
- Автоматическое определение рабочего пространства
- Хранение пользовательских данных проекта (глоссарии, спецификации)
- Отслеживание решений и прогресса
- Поддержка кэширования промптов для совместимых провайдеров LLM

## Примеры использования

```
Initialize according to custom instructions
```

```
Create a projectBrief.md file to bootstrap initial project context
```

## Ресурсы

- [GitHub Repository](https://github.com/GreatScottyMac/context-portal)

## Примечания

ConPort включает файлы стратегий для различных IDE окружений (Roo Code, CLine, Windsurf Cascade) с специфическими пользовательскими инструкциями. Сервер автоматически создает базу данных SQLite для каждого рабочего пространства и поддерживает автоматическое определение workspace. Файл projectBrief.md в корне рабочего пространства может использоваться для создания начального контекста проекта.