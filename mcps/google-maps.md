---
title: Google Maps MCP сервер
description: Python-based MCP сервер, который использует Google Maps и Places API
  для ответов на запросы о местных бизнесах и туристических достопримечательностях в Индии.
tags:
- API
- Search
- Integration
author: Mastan1301
featured: false
---

Python-based MCP сервер, который использует Google Maps и Places API для ответов на запросы о местных бизнесах и туристических достопримечательностях в Индии.

## Установка

### UVX

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uvx google-mcp-server
```

### Из исходников

```bash
git clone <your-fork-url>
cd google_maps_mcp
uv build
export GOOGLE_MAPS_API_KEY=your_api_key_here
uvx dist/google_maps_mcp-1.0.0-py3-none-any.whl
```

## Конфигурация

### Visual Studio Code

```json
"mcp": {
        "servers": {
            "google_maps_mcp_server":{
                "type": "stdio",
                "command": "uvx",
                "args": ["google-maps-mcp"],
                "env": {
                    "GOOGLE_MAPS_API_KEY": "<your google maps API key>"
                }
            }
        }
    }
```

## Возможности

- Запросы к Google Maps для поиска мест, ресторанов, туристических достопримечательностей и многого другого
- Легкая настройка с вашим собственным Google Maps API ключом
- Модульная, поддерживаемая и тестируемая кодовая база
- Готов для расширения и вклада в разработку

## Переменные окружения

### Обязательные
- `GOOGLE_MAPS_API_KEY` - Google Maps API ключ для доступа к Google Maps и Places API

## Примеры использования

```
What are the best cafes in Bangalore?
```

```
Top-rated tourist places near Hyderabad
```

## Ресурсы

- [GitHub Repository](https://github.com/Mastan1301/google_maps_mcp)

## Примечания

Требует Python 3.8+ и фокусируется специально на бизнесах и туристических достопримечательностях в Индии. Для локальной разработки убедитесь, что ~/.local/bin находится в вашей переменной окружения PATH.