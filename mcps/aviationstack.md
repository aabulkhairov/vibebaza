---
title: Aviationstack MCP сервер
description: MCP сервер, который предоставляет инструменты для работы с AviationStack API — получение данных о рейсах в реальном времени и будущих полётах, типах воздушных судов и подробной информации о самолётах.
tags:
- API
- Analytics
- Integration
author: Pradumnasaraf
featured: false
---

MCP сервер, который предоставляет инструменты для работы с AviationStack API — получение данных о рейсах в реальном времени и будущих полётах, типах воздушных судов и подробной информации о самолётах.

## Установка

### UVX (рекомендуется)

```bash
uvx aviationstack-mcp
```

### Из исходного кода

```bash
uv --directory /path/to/aviationstack-mcp/src/aviationstack_mcp run -m aviationstack_mcp mcp run
```

## Конфигурация

### Используя uvx (рекомендуется)

```json
{
  "mcpServers": {
    "Aviationstack MCP": {
      "command": "uvx",
      "args": [
        "aviationstack-mcp"
      ],
      "env": {
        "AVIATION_STACK_API_KEY": "<your-api-key>"
      }
    }
  }
}
```

### Локальный репозиторий

```json
{
  "mcpServers": {
    "Aviationstack MCP": {
      "command": "uv",
      "args": [
        "--directory",
        "/path/to/aviationstack-mcp/src/aviationstack_mcp",
        "run",
        "-m",
        "aviationstack_mcp",
        "mcp",
        "run"
      ],
      "env": {
        "AVIATION_STACK_API_KEY": "<your-api-key>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `flights_with_airline` | Получить случайную выборку рейсов для конкретной авиакомпании |
| `flight_arrival_departure_schedule` | Получить расписание прилётов или вылетов для указанного аэропорта и авиакомпании |
| `future_flights_arrival_departure_schedule` | Получить расписание будущих рейсов для указанного аэропорта, авиакомпании и даты |
| `random_aircraft_type` | Получить случайные типы воздушных судов |
| `random_airplanes_detailed_info` | Получить подробную информацию о случайных самолётах |
| `random_countries_detailed_info` | Получить подробную информацию о случайных странах |
| `random_cities_detailed_info` | Получить подробную информацию о случайных городах |

## Возможности

- Получение рейсов для конкретной авиакомпании
- Получение расписания прилётов и вылетов для аэропортов
- Получение расписания будущих рейсов
- Получение случайных типов воздушных судов
- Получение подробной информации о случайных самолётах
- Получение подробной информации о случайных странах
- Получение подробной информации о случайных городах

## Переменные окружения

### Обязательные
- `AVIATION_STACK_API_KEY` - API ключ для AviationStack API (можно получить БЕСПЛАТНЫЙ ключ на aviationstack.com)

## Ресурсы

- [GitHub Repository](https://github.com/Pradumnasaraf/aviationstack-mcp)

## Примечания

Требует Python 3.13 или новее и пакетный менеджер uv. Использует класс FastMCP и функции, декорированные с @mcp.tool(). Распространяется под лицензией MIT License.