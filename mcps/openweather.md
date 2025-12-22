---
title: OpenWeather MCP сервер
description: Простой MCP сервис, который предоставляет актуальную информацию о погоде и 5-дневные прогнозы через бесплатный OpenWeatherMap API с поддержкой различных единиц измерения и языков.
tags:
- API
- Monitoring
- Productivity
- Integration
author: mschneider82
featured: false
---

Простой MCP сервис, который предоставляет актуальную информацию о погоде и 5-дневные прогнозы через бесплатный OpenWeatherMap API с поддержкой различных единиц измерения и языков.

## Установка

### Из исходного кода

```bash
git clone https://github.com/mschneider82/mcp-openweather.git
cd mcp-openweather
go build -o mcp-weather
```

### Smithery

```bash
npx -y @smithery/cli install @mschneider82/mcp-openweather --client claude
```

## Конфигурация

### Claude Desktop

```json
"mcpServers": {
    "mcp-openweather": {
        "command": "/home/YOURUSER/git/mcp-openweather/mcp-openweather",
        "env": {
            "OWM_API_KEY": "PUT_API_KEY_HERE"
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `weather` | Получает текущие погодные условия и 5-дневный прогноз для указанного города с настраиваемыми единицами измерения... |

## Возможности

- Текущие погодные условия
- 5-дневный прогноз погоды
- Настраиваемые единицы измерения (Цельсий/Фаренгейт/Кельвин)
- Поддержка нескольких языков
- Простая интеграция с MCP

## Переменные окружения

### Обязательные
- `OWM_API_KEY` - OpenWeatherMap API ключ для доступа к данным о погоде

## Примеры использования

```
Get weather for Berlin
```

```
Show weather forecast for München in Celsius
```

```
Get current weather conditions with German language support
```

## Ресурсы

- [GitHub Repository](https://github.com/mschneider82/mcp-openweather)

## Примечания

Требует Go 1.20+ и OpenWeatherMap API ключ. Параметры инструмента включают город (обязательно), единицы измерения (опционально: c|f|k) и язык (опционально: en|de|fr|...). Предоставляет детальную обработку ошибок для типичных сценариев, таких как отсутствующие API ключи, неверные города и проблемы с сетью.