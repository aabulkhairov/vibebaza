---
title: Scholarly MCP сервер
description: MCP сервер для поиска точных академических статей из научных источников, таких как arXiv, с планами добавления других академических поставщиков.
tags:
- Search
- API
- Analytics
- Productivity
author: adityak74
featured: true
install_command: npx -y @smithery/cli install mcp-scholarly --client claude
---

MCP сервер для поиска точных академических статей из научных источников, таких как arXiv, с планами добавления других академических поставщиков.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-scholarly --client claude
```

### UV/UVX

```bash
uvx mcp-scholarly
```

### Docker

```bash
docker run --rm -i mcp/scholarly
```

### Разработка

```bash
uv sync
uv build
uv publish
```

## Конфигурация

### Claude Desktop - Опубликованная версия

```json
"mcpServers": {
  "mcp-scholarly": {
    "command": "uvx",
    "args": [
      "mcp-scholarly"
    ]
  }
}
```

### Claude Desktop - Версия для разработки

```json
"mcpServers": {
  "mcp-scholarly": {
    "command": "uv",
    "args": [
      "--directory",
      "/Users/adityakarnam/PycharmProjects/mcp-scholarly/mcp-scholarly",
      "run",
      "mcp-scholarly"
    ]
  }
}
```

### Claude Desktop - Docker

```json
"mcpServers": {
  "mcp-scholarly": {
    "command": "docker",
    "args": [
      "run", "--rm", "-i",
      "mcp/scholarly"
    ]
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search-arxiv` | Поиск статей на arXiv по заданному ключевому слову (принимает обязательный строковый аргумент с ключевым словом) |

## Возможности

- Поиск точных академических статей
- Интеграция с arXiv для научного контента
- Планируется добавление других научных поставщиков

## Ресурсы

- [GitHub Repository](https://github.com/adityak74/mcp-scholarly)

## Примечания

Для отладки используйте MCP Inspector с командой: npx @modelcontextprotocol/inspector uv --directory /path/to/project run mcp-scholarly. Для публикации требуются учетные данные PyPI через переменные окружения или флаги командной строки.