---
title: Apple Script MCP сервер
description: Сервер Model Context Protocol, который позволяет выполнять AppleScript код для взаимодействия с Mac приложениями, файлами и системными функциями через команды на естественном языке.
tags:
- Productivity
- Integration
- Code
- API
author: Community
featured: false
---

Сервер Model Context Protocol, который позволяет выполнять AppleScript код для взаимодействия с Mac приложениями, файлами и системными функциями через команды на естественном языке.

## Установка

### NPX

```bash
npx @peakmojo/applescript-mcp
```

### Python с UV

```bash
brew install uv
git clone ...
```

## Конфигурация

### Claude Desktop - Node.js

```json
{
  "mcpServers": {
    "applescript_execute": {
      "command": "npx",
      "args": [
        "@peakmojo/applescript-mcp"
      ]
    }
  }
}
```

### Claude Desktop - Python

```json
{
  "mcpServers": {
    "applescript_execute": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/your/repo",
        "run",
        "src/applescript_mcp/server.py"
      ]
    }
  }
}
```

### Конфигурация Docker

```json
{
  "mcpServers": {
    "applescript_execute": {
      "command": "npx",
      "args": [
        "@peakmojo/applescript-mcp",
        "--remoteHost", "host.docker.internal",
        "--remoteUser", "yourusername",
        "--remotePassword", "yourpassword"
      ]
    }
  }
}
```

## Возможности

- Запуск AppleScript для доступа к Mac приложениям и данным
- Взаимодействие с Заметками, Календарем, Контактами, Сообщениями и многим другим
- Поиск файлов через Spotlight или Finder
- Чтение/запись содержимого файлов и выполнение shell команд
- Поддержка удаленного выполнения через SSH

## Примеры использования

```
Create a reminder for me to call John tomorrow at 10am
```

```
Add a new meeting to my calendar for Friday from 2-3pm titled "Team Review"
```

```
Create a new note titled "Meeting Minutes" with today's date
```

```
Show me all files in my Downloads folder from the past week
```

```
What's my current battery percentage?
```

## Ресурсы

- [GitHub Repository](https://github.com/peakmojo/applescript-mcp)

## Примечания

Поддерживает реализации как на Node.js, так и на Python. Использование Docker требует включения SSH на Mac с правильными учетными данными. Основной код составляет менее 100 строк, что подчеркивает простоту и минимальную настройку.