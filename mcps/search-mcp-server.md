---
title: Search MCP Server MCP сервер
description: MCP сервер, который позволяет искать и находить существующие MCP серверы из официального GitHub репозитория с живым парсингом и настраиваемым кэшированием.
tags:
- Search
- Web Scraping
- API
- Integration
- Productivity
author: krzysztofkucmierz
featured: false
---

MCP сервер, который позволяет искать и находить существующие MCP серверы из официального GitHub репозитория с живым парсингом и настраиваемым кэшированием.

## Установка

### PyPI с UV

```bash
pip install uv
uv venv
source .venv/bin/activate
uv pip install search-mcp-server
search-mcp-server --sse
```

### Из исходного кода

```bash
git clone https://github.com/<your-account>/search-mcp-server.git
cd search-mcp-server
uv sync
uv run python mcp_server.py --sse
```

## Конфигурация

### VSCode MCP расширение

```json
{
    "servers": {
        "Search MCP server": { "url": "http://127.0.0.1:8000/sse", "type": "http" }
    },
    "inputs": []
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_mcp_servers` | Поиск подходящих MCP серверов по имени, описанию или категории |
| `get_mcp_server_categories` | Получение доступных категорий MCP серверов |

## Возможности

- Поиск MCP серверов по имени, описанию или категории
- Динамические данные с живым парсингом из официального GitHub репозитория
- Быстрая работа и кэширование с настраиваемым кэшем (по умолчанию: 6 часов)
- Ресурсы доступны по адресам mcp://servers/list и mcp://servers/categories

## Ресурсы

- [GitHub Repository](https://github.com/krzysztofkucmierz/search-mcp-server)

## Примечания

Сервер поддерживает как SSE режим (HTTP endpoint), так и stdio режим. Опции командной строки включают --sse для SSE режима, --port для кастомного порта (по умолчанию 8000), --cache-timeout для длительности кэша (по умолчанию 21600 секунд), и --help для доступных опций. Можно отлаживать с помощью MCP Inspector.