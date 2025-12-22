---
title: mcp_weather MCP сервер
description: MCP сервер, который предоставляет комплексную информацию о погоде и качестве воздуха через Open-Meteo API, поддерживая несколько режимов транспорта включая stdio, HTTP SSE и потоковый HTTP.
tags:
- API
- Web Scraping
- Analytics
- Integration
- Monitoring
author: isdaniel
featured: false
---

MCP сервер, который предоставляет комплексную информацию о погоде и качестве воздуха через Open-Meteo API, поддерживая несколько режимов транспорта включая stdio, HTTP SSE и потоковый HTTP.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @isdaniel/mcp_weather_server
```

### Pip

```bash
pip install mcp_weather_server
```

### HTTP сервер (с зависимостями)

```bash
pip install mcp_weather_server starlette uvicorn
```

## Конфигурация

### MCP клиент (cline_mcp_settings.json)

```json
{
  "mcpServers": {
    "weather": {
      "command": "python",
      "args": [
        "-m",
        "mcp_weather_server"
      ],
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_current_weather` | Получить текущую погоду для города с комплексными метриками включая температуру, влажность, ветер, ... |
| `get_weather_by_datetime_range` | Получить данные о погоде за диапазон дат с почасовыми деталями и анализом трендов |
| `get_weather_details` | Получить детальную информацию о погоде в виде структурированных JSON данных для программного использования |
| `get_air_quality` | Получить информацию о качестве воздуха с уровнями загрязнителей и рекомендациями по здоровью |
| `get_air_quality_details` | Получить детальные данные о качестве воздуха в виде структурированного JSON для анализа |
| `get_current_datetime` | Получить текущее время в любой временной зоне используя имена временных зон IANA |
| `get_timezone_info` | Получить информацию о временной зоне включая смещение и детали летнего времени |
| `convert_time` | Конвертировать время между различными временными зонами |

## Возможности

- Текущая погода с температурой, влажностью, ветром, осадками, UV индексом и видимостью
- Исторические данные о погоде с почасовыми деталями за диапазоны дат
- Мониторинг качества воздуха с PM2.5, PM10, озоном и другими загрязнителями
- Рекомендации и советы по здоровью на основе качества воздуха
- Операции с временными зонами и конвертация времени
- Несколько режимов транспорта: stdio, HTTP SSE и потоковый HTTP
- Не требует API ключ - использует бесплатный Open-Meteo API
- Режимы работы с состоянием и без состояния для HTTP
- RESTful API эндпоинты через интеграцию Starlette

## Примеры использования

```
What's the current weather in Tokyo?
```

```
Get weather data for Paris from January 1st to January 7th
```

```
What's the air quality in Beijing right now?
```

```
What time is it in New York?
```

```
Convert 2PM UTC to Tokyo time
```

## Ресурсы

- [GitHub Repository](https://github.com/isdaniel/mcp_weather_server)

## Примечания

Поддерживает три режима сервера: stdio (по умолчанию для десктопных клиентов), SSE (для веб приложений) и streamable-http (современный MCP протокол). Может работать с настраиваемыми хостом/портом и режимом отладки. Предоставляет как читаемые человеком ответы, так и структурированные JSON данные для программного использования.