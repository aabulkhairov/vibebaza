---
title: Basic Memory MCP сервер
description: Локальная система управления знаниями, которая строит семантический граф
  из Markdown файлов, обеспечивая постоянную память в разговорах с LLM через
  естественные языковые взаимодействия.
tags:
- AI
- Productivity
- Storage
- Database
- Code
author: basicmachines-co
featured: true
---

Локальная система управления знаниями, которая строит семантический граф из Markdown файлов, обеспечивая постоянную память в разговорах с LLM через естественные языковые взаимодействия.

## Установка

### UV Tool

```bash
uv tool install basic-memory
```

### Smithery

```bash
npx -y @smithery/cli install @basicmachines-co/basic-memory --client claude
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "basic-memory": {
      "command": "uvx",
      "args": [
        "basic-memory",
        "mcp"
      ]
    }
  }
}
```

### Claude Desktop с проектом

```json
{
  "mcpServers": {
    "basic-memory": {
      "command": "uvx",
      "args": [
        "basic-memory",
        "mcp",
        "--project",
        "your-project-name"
      ]
    }
  }
}
```

### Настройки пользователя VS Code

```json
{
  "mcp": {
    "servers": {
      "basic-memory": {
        "command": "uvx",
        "args": ["basic-memory", "mcp"]
      }
    }
  }
}
```

### Рабочая область VS Code

```json
{
  "servers": {
    "basic-memory": {
      "command": "uvx",
      "args": ["basic-memory", "mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `write_note` | Создавать или обновлять заметки |
| `read_note` | Читать заметки по названию или permalink |
| `read_content` | Читать сырое содержимое файлов (текст, изображения, бинарные файлы) |
| `view_note` | Просматривать заметки как форматированные артефакты |
| `edit_note` | Редактировать заметки пошагово |
| `move_note` | Перемещать заметки с сохранением целостности базы данных |
| `delete_note` | Удалять заметки из базы знаний |
| `build_context` | Навигация по графу знаний через memory:// URL |
| `recent_activity` | Находить недавно обновленную информацию |
| `list_directory` | Просматривать содержимое директорий с фильтрацией |
| `search` | Поиск по всей базе знаний |
| `list_memory_projects` | Показать все доступные проекты |
| `create_memory_project` | Создавать новые проекты |
| `get_current_project` | Показать статистику текущего проекта |
| `sync_status` | Проверить статус синхронизации |

## Возможности

- Локальное хранение в Markdown файлах
- Двунаправленное чтение и запись между людьми и LLM
- Структурированный граф знаний с семантическими паттернами
- Синхронизация в реальном времени между устройствами
- Совместимость с Obsidian и другими Markdown редакторами
- База данных SQLite для индексации и поиска
- Облачная синхронизация с кроссплатформенной поддержкой
- Управление несколькими проектами
- Отслеживание семантических связей и наблюдений
- Визуализация знаний с генерацией canvas

## Примеры использования

```
Create a note about coffee brewing methods
```

```
What do I know about pour over coffee?
```

```
Find information about Ethiopian beans
```

```
Create a note about our project architecture decisions
```

```
Find information about JWT authentication in my notes
```

## Ресурсы

- [GitHub Repository](https://github.com/basicmachines-co/basic-memory)

## Примечания

Поддерживает два типа баз данных (SQLite и Postgres). Доступен облачный сервис с ценами для ранних сторонников (скидка 25% навсегда). Файлы по умолчанию хранятся в ~/basic-memory. Совместим с Claude Desktop, VS Code и другими MCP клиентами. Включает CLI инструменты для синхронизации, импорта и управления проектами.