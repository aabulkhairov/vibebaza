---
title: man-mcp-server MCP сервер
description: MCP сервер, который предоставляет доступ к Linux man страницам,
  позволяя AI-ассистентам искать, получать и исследовать системную документацию
  прямо с вашей локальной машины.
tags:
- Documentation
- DevOps
- Search
- Productivity
- API
author: Community
featured: false
---

MCP сервер, который предоставляет доступ к Linux man страницам, позволяя AI-ассистентам искать, получать и исследовать системную документацию прямо с вашей локальной машины.

## Установка

### MCPB Bundle

```bash
git clone https://github.com/guyru/man-mcp.git
cd man-mcp
make build
```

### UV (рекомендуется)

```bash
git clone https://github.com/guyru/man-mcp.git
cd man-mcp
uv sync
```

### Pip

```bash
git clone https://github.com/guyru/man-mcp.git
cd man-mcp
pip install .
```

## Конфигурация

### VS Code с UV

```json
{
  "servers": {
    "man-mcp-server": {
      "type": "stdio",
      "command": "uv",
      "args": [
        "run",
        "--directory",
        "/path/to/man-mcp",
        "server/main.py"
      ]
    }
  }
}
```

### VS Code с Python

```json
{
  "servers": {
    "man-mcp-server": {
      "type": "stdio",
      "command": "python3",
      "args": ["/path/to/man-mcp/server/main.py"],
      "env": {
        "PYTHONPATH": "/path/to/man-mcp/server/lib"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_man_pages` | Поиск man страниц по ключевому слову или теме |
| `get_man_page` | Получение полного содержимого конкретной man страницы |
| `list_man_sections` | Список всех доступных разделов man страниц с описаниями |

## Возможности

- Поиск man страниц по ключевому слову или названию команды с использованием apropos
- Получение полного содержимого man страниц по имени и опциональному разделу
- Просмотр доступных разделов man страниц (1-9) с описаниями
- Чистое форматирование с содержимым man страниц, подготовленным для потребления AI
- Асинхронные операции с защитой от таймаутов
- MCP ресурсы с man:// URI
- Комплексная обработка ошибок с плавными откатами

## Примеры использования

```
Find pages about permissions
```

```
Find networking-related pages
```

```
Get ls man page
```

```
Get chmod from section 1 specifically
```

```
Get printf from section 3 (C library)
```

## Ресурсы

- [GitHub Repository](https://github.com/guyru/man-mcp-server)

## Примечания

Требует Linux со стандартной системой man страниц и командами man/apropos. Поддерживает MCPB bundles для интеграции с Claude Desktop. Предоставляет man страницы как ресурсы, используя man:// URI для прямого доступа к документации.