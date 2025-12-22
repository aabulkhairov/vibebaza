---
title: MeasureSpace MCP сервер
description: MCP сервер, который предоставляет прогнозы погоды, климата, качества воздуха и геокодинг от measurespace.io для AI-ассистентов.
tags:
- API
- Analytics
- Integration
author: MeasureSpace
featured: false
install_command: npx -y @smithery/cli install @MeasureSpace/measure-space-mcp-server
  --client claude
---

MCP сервер, который предоставляет прогнозы погоды, климата, качества воздуха и геокодинг от measurespace.io для AI-ассистентов.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @MeasureSpace/measure-space-mcp-server --client claude
```

### Из исходного кода

```bash
git clone git@github.com:MeasureSpace/measure-space-mcp-server.git
cd measure-space-mcp-server
uv venv
uv pip install -e .
```

### Запуск сервера

```bash
python main.py
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "MeasureSpace": {
      "command": "/<your_uv_path>/uv",
      "args": [
        "--directory",
        "/<your-measure-space-mcp-server-folder-path>/measure-space-mcp-server",
        "run",
        "main.py"
      ]
    }
  }
}
```

## Возможности

- Почасовой прогноз погоды на следующие 5 дней
- Ежедневный прогноз погоды на следующие 15 дней
- Ежедневный прогноз климата на следующие 9 месяцев
- Почасовой и ежедневный прогноз качества воздуха на следующие 4 дня
- Сервис геокодинга для поиска широты и долготы по названиям городов
- Сервис геокодинга для поиска ближайшего города по координатам
- Информация о часовых поясах
- Астрономические данные (восход, закат)

## Переменные окружения

### Опциональные
- `GEOCODING_API_KEY` - API ключ для геокодинга от measurespace.io
- `HOURLY_WEATHER_API_KEY` - API ключ для почасовых прогнозов погоды от measurespace.io
- `DAILY_WEATHER_API_KEY` - API ключ для ежедневных прогнозов погоды от measurespace.io
- `AIR_QUALITY_API_KEY` - API ключ для прогнозов качества воздуха от measurespace.io

## Ресурсы

- [GitHub Repository](https://github.com/MeasureSpace/measure-space-mcp-server)

## Примечания

Требуется Python 3.12+ и менеджер пакетов uv. API ключи нужны только для тех сервисов, которые вы планируете использовать. Сервер по умолчанию запускается на http://localhost:8000.