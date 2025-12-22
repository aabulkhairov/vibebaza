---
title: Geolocation MCP сервер
description: MCP сервер, который предоставляет геолокационные сервисы, включая интеграцию с WalkScore API для оценки пешеходной доступности, транспортной доступности и велосипедной инфраструктуры.
tags:
- API
- Analytics
- Productivity
author: jackyang25
featured: false
---

MCP сервер, который предоставляет геолокационные сервисы, включая интеграцию с WalkScore API для оценки пешеходной доступности, транспортной доступности и велосипедной инфраструктуры.

## Установка

### uv (рекомендуется)

```bash
uvx mcp-server-geolocation
```

### pip

```bash
pip install mcp-server-geolocation
```

## Конфигурация

### Claude.app

```json
{
  "mcpServers": {
    "geolocation": {
      "command": "uvx",
      "args": ["mcp-server-geolocation"],
      "env": {
        "WALKSCORE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### VS Code

```json
{
  "mcp": {
    "servers": {
      "geolocation": {
        "command": "uvx",
        "args": ["mcp-server-geolocation"],
        "env": {
          "WALKSCORE_API_KEY": "your_api_key_here"
        }
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_transit_stops` | Получить ближайшие остановки общественного транспорта для локации |
| `get_walkscore` | Получить WalkScore, TransitScore и BikeScore для локации |

## Возможности

- Остановки транспорта: поиск ближайших остановок общественного транспорта для любой локации
- WalkScore: получение оценки пешеходной доступности для любого адреса
- TransitScore: получение оценки доступности общественного транспорта
- BikeScore: получение оценки велосипедной инфраструктуры для локаций
- На основе геолокации: работает с адресами, координатами или и тем, и другим

## Переменные окружения

### Обязательные
- `WALKSCORE_API_KEY` - API ключ от walkscore.com для доступа к сервисам WalkScore, TransitScore и BikeScore

## Примеры использования

```
Find transit stops near 40.7136, -73.9909
```

```
What's the walkability score for 123 Main St, Seattle, WA?
```

## Ресурсы

- [GitHub Repository](https://github.com/jackyang25/geolocation-mcp-server)

## Примечания

Требуется WalkScore API ключ от walkscore.com/professional/api.php. Поддерживает ввод через строки адресов, координаты широты/долготы или и то, и другое для лучшей точности. Предоставляет оценки от 0 до 100 для метрик пешеходной доступности, транспортной доступности и велосипедной инфраструктуры.