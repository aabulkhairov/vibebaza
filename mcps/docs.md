---
title: Docs MCP сервер
description: MCP сервер, который предоставляет доступ к документации для LLM из локальных файлов или удаленных URL, позволяя AI агентам запрашивать и получать содержимое документации.
tags:
- Documentation
- API
- Integration
- Productivity
- AI
author: da1z
featured: false
---

MCP сервер, который предоставляет доступ к документации для LLM из локальных файлов или удаленных URL, позволяя AI агентам запрашивать и получать содержимое документации.

## Установка

### NPX

```bash
npx -y docsmcp '--source=Model Context Protocol (MCP)|https://modelcontextprotocol.io/llms-full.txt'
```

## Конфигурация

### Cursor

```json
{
  "mcpServers": {
    "docs-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "docsmcp",
        "'--source=Model Context Protocol (MCP)|https://modelcontextprotocol.io/llms-full.txt'"
      ]
    }
  }
}
```

### VS Code

```json
{
  "servers": {
    "documentation-mcp-server": {
      "type": "stdio",
      "command": "npx",
      "args": [
        "-y",
        "docsmcp",
        "--source=Model Context Protocol (MCP)|https://modelcontextprotocol.io/llms-full.txt"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `getDocumentationSources` | Показывает все доступные источники документации, которые были настроены |
| `getDocumentation` | Получает и парсит документацию из указанного URL или локального файла |

## Возможности

- Доступ к документации из локальных файлов или удаленных URL
- Поддержка формата llms.txt
- Запрос и получение содержимого документации
- Интеграция с Cursor и VS Code через MCP

## Ресурсы

- [GitHub Repository](https://github.com/da1z/docsmcp)

## Примечания

При указании источника, содержащего пробелы, обязательно заключайте всю строку в кавычки. Сервер принимает источники в формате 'Название|URL', где Название — это имя источника документации, а URL — его местоположение.