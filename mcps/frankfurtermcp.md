---
title: FrankfurterMCP сервер
description: MCP сервер, который предоставляет доступ к Frankfurter API для получения актуальных валютных курсов, исторических данных и конвертации валют, используя данные из таких источников, как Европейский центральный банк.
tags:
- Finance
- API
- Analytics
author: anirbanbasu
featured: false
---

MCP сервер, который предоставляет доступ к Frankfurter API для получения актуальных валютных курсов, исторических данных и конвертации валют, используя данные из таких источников, как Европейский центральный банк.

## Установка

### Из исходного кода с uv

```bash
git clone https://github.com/anirbanbasu/frankfurtermcp
cd frankfurtermcp
just install
uv run frankfurtermcp
```

### PyPI с pip

```bash
pip install frankfurtermcp
python -m frankfurtermcp.server
```

### Docker

```bash
docker build -t frankfurtermcp -f local.dockerfile .
docker run -it --rm -p 8000:8000/tcp --env-file .env.template --expose 8000 frankfurtermcp
```

## Конфигурация

### Claude Desktop (uv)

```json
{
    "command": "uv",
    "args": [
        "run",
        "frankfurtermcp"
    ]
}
```

### Claude Desktop (Python)

```json
{
    "command": "python3.12",
    "args": [
        "-m",
        "frankfurtermcp.server"
    ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_supported_currencies` | Получить список валют, поддерживаемых Frankfurter API |
| `get_latest_exchange_rates` | Получить актуальные валютные курсы в определенных валютах для заданной базовой валюты |
| `convert_currency_latest` | Конвертировать сумму из одной валюты в другую, используя актуальные валютные курсы |
| `get_historical_exchange_rates` | Получить исторические валютные курсы для конкретной даты или диапазона дат в определенных валютах для заданной... |
| `convert_currency_specific_date` | Конвертировать сумму из одной валюты в другую, используя валютные курсы на конкретную дату |

## Возможности

- Актуальные валютные курсы от Европейского центрального банка и других источников
- Исторические данные валютных курсов и временные ряды
- Расчеты конвертации валют
- LRU и TTL кеширование для улучшенной производительности
- Поддержка самостоятельно размещенных экземпляров Frankfurter API
- Множественные варианты транспорта (stdio, SSE, streamable HTTP)
- Доступные облачные варианты размещения

## Переменные окружения

### Опциональные
- `LOG_LEVEL` - Уровень логирования (по умолчанию: INFO)
- `HTTPX_TIMEOUT` - Таймаут HTTP клиента в секундах для Frankfurter API (по умолчанию: 5.0)
- `HTTPX_VERIFY_SSL` - Включить/отключить проверку SSL сертификатов (по умолчанию: True)
- `FAST_MCP_HOST` - Хост для привязки MCP сервера (по умолчанию: localhost)
- `FAST_MCP_PORT` - Порт для прослушивания MCP сервера (по умолчанию: 8000)
- `MCP_SERVER_TRANSPORT` - Тип транспорта сервера: stdio, sse или streamable-http (по умолчанию: stdio)
- `MCP_SERVER_INCLUDE_METADATA_IN_RESPONSE` - Включать дополнительные метаданные в MCP ответы (по умолчанию: True)
- `FRANKFURTER_API_URL` - URL конечной точки API для сервиса Frankfurter (по умолчанию: https://api.frankfurter.dev/v1)

## Примеры использования

```
Какие актуальные курсы обмена EUR к USD?
```

```
Конвертируй 100 USD в EUR, используя сегодняшние курсы
```

```
Каким был курс обмена между GBP и JPY 1 января 2023 года?
```

```
Покажи мне исторические курсы обмена EUR к нескольким валютам за прошлую неделю
```

```
Какие валюты поддерживаются Frankfurter API?
```

## Ресурсы

- [GitHub Repository](https://github.com/anirbanbasu/frankfurtermcp)

## Примечания

Облачные варианты размещения доступны на FastMCP Cloud (https://frankfurtermcp.fastmcp.app/mcp), Glama.AI и Smithery.AI. Поддерживает самостоятельно размещенные экземпляры Frankfurter API и включает кеширование для улучшенной производительности.