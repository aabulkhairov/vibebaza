---
title: Tripadvisor MCP сервер
description: MCP сервер, который предоставляет доступ к данным о местоположениях, отзывах и фотографиях Tripadvisor через стандартизированные MCP интерфейсы, позволяя AI-ассистентам искать туристические направления и впечатления.
tags:
- API
- Search
- Integration
- Analytics
- Web Scraping
author: pab1it0
featured: false
---

MCP сервер, который предоставляет доступ к данным о местоположениях, отзывах и фотографиях Tripadvisor через стандартизированные MCP интерфейсы, позволяя AI-ассистентам искать туристические направления и впечатления.

## Установка

### UV Package Manager

```bash
uv venv
source .venv/bin/activate  # On Unix/macOS
.venv\Scripts\activate     # On Windows
uv pip install -e .
```

### Docker Build

```bash
docker build -t tripadvisor-mcp-server .
```

### Docker Run

```bash
docker run -it --rm \
  -e TRIPADVISOR_API_KEY=your_api_key_here \
  tripadvisor-mcp-server
```

### Docker Compose

```bash
docker-compose up
```

## Конфигурация

### Claude Desktop - UV

```json
{
  "mcpServers": {
    "tripadvisor": {
      "command": "uv",
      "args": [
        "--directory",
        "<full path to tripadvisor-mcp directory>",
        "run",
        "src/tripadvisor_mcp/main.py"
      ],
      "env": {
        "TRIPADVISOR_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Claude Desktop - Docker

```json
{
  "mcpServers": {
    "tripadvisor": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-e", "TRIPADVISOR_API_KEY",
        "tripadvisor-mcp-server"
      ],
      "env": {
        "TRIPADVISOR_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_locations` | Поиск местоположений по текстовому запросу, категории и другим фильтрам |
| `search_nearby_locations` | Поиск местоположений рядом с определенными координатами |
| `get_location_details` | Получение детальной информации о местоположении |
| `get_location_reviews` | Получение отзывов о местоположении |
| `get_location_photos` | Получение фотографий местоположения |

## Возможности

- Поиск местоположений (отели, рестораны, достопримечательности) на Tripadvisor
- Получение детальной информации о конкретных местоположениях
- Получение отзывов и фотографий местоположений
- Поиск ближайших местоположений на основе координат
- Аутентификация через API Key
- Поддержка контейнеризации Docker
- Предоставление интерактивных инструментов для AI-ассистентов
- Настраиваемый список инструментов

## Переменные окружения

### Обязательные
- `TRIPADVISOR_API_KEY` - Обязательный API ключ для доступа к Tripadvisor Content API

## Ресурсы

- [GitHub Repository](https://github.com/pab1it0/tripadvisor-mcp)

## Примечания

Требуется API ключ Tripadvisor Content API из портала разработчиков Tripadvisor. Если вы видите ошибку 'Error: spawn uv ENOENT' в Claude Desktop, укажите полный путь к uv или установите переменную окружения NO_UV=1.