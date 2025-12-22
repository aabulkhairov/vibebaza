---
title: Everything Search MCP сервер
description: MCP сервер, который обеспечивает быстрый поиск файлов в Windows,
  macOS и Linux, используя специализированные утилиты поиска для каждой платформы (Everything SDK, mdfind
  и locate).
tags:
- Search
- Productivity
- Integration
- Storage
author: Community
featured: false
install_command: npx -y @smithery/cli install mcp-server-everything-search --client
  claude
---

MCP сервер, который обеспечивает быстрый поиск файлов в Windows, macOS и Linux, используя специализированные утилиты поиска для каждой платформы (Everything SDK, mdfind и locate).

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-server-everything-search --client claude
```

### uv (рекомендуется)

```bash
uvx mcp-server-everything-search
```

### PIP

```bash
pip install mcp-server-everything-search
python -m mcp_server_everything_search
```

## Конфигурация

### Windows (используя uvx)

```json
"mcpServers": {
  "everything-search": {
    "command": "uvx",
    "args": ["mcp-server-everything-search"],
    "env": {
      "EVERYTHING_SDK_PATH": "path/to/Everything-SDK/dll/Everything64.dll"
    }
  }
}
```

### Windows (используя pip установку)

```json
"mcpServers": {
  "everything-search": {
    "command": "python",
    "args": ["-m", "mcp_server_everything_search"],
    "env": {
      "EVERYTHING_SDK_PATH": "path/to/Everything-SDK/dll/Everything64.dll"
    }
  }
}
```

### Linux и macOS (uvx)

```json
"mcpServers": {
  "everything-search": {
    "command": "uvx",
    "args": ["mcp-server-everything-search"]
  }
}
```

### Linux и macOS (pip)

```json
"mcpServers": {
  "everything-search": {
    "command": "python",
    "args": ["-m", "mcp_server_everything_search"]
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search` | Поиск файлов и папок по всей системе с возможностями, специфичными для каждой платформы (Windows: пол... |

## Возможности

- Кроссплатформенный поиск файлов (Windows, macOS, Linux)
- Специализированные возможности поиска для каждой платформы (Everything SDK на Windows, mdfind на macOS, locate на Linux)
- Множественные параметры поиска: чувствительность к регистру, поиск целых слов, поддержка регулярных выражений
- Гибкие опции сортировки (имя файла, путь, размер, расширение, даты)
- Настраиваемое ограничение результатов (до 1000 результатов)
- Поиск по полному пути или только по имени файла
- Метаданные файлов в результатах (путь, размер, дата модификации)

## Переменные окружения

### Обязательные
- `EVERYTHING_SDK_PATH` - Путь к DLL файлу Everything SDK (только для Windows)

## Примеры использования

```
Поиск Python файлов: {"query": "*.py", "max_results": 50, "sort_by": 6}
```

```
Найти недавно измененные Python файлы: {"query": "ext:py datemodified:today", "max_results": 10}
```

## Ресурсы

- [GitHub Repository](https://github.com/mamertofabian/mcp-everything-search)

## Примечания

Требует специфичных для платформы предварительных условий: утилита Everything + SDK на Windows, plocate/mlocate на Linux, дополнительная настройка не нужна на macOS. Смотрите SEARCH_SYNTAX.md для подробного руководства по синтаксису поиска. Лицензия MIT. Не связан с voidtools.