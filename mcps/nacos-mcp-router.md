---
title: Nacos MCP Router MCP сервер
description: MCP сервер, который предоставляет инструменты для поиска, установки и проксирования других MCP серверов с расширенными возможностями поиска, включая векторный поиск по сходству и агрегацию результатов от нескольких провайдеров.
tags:
- Search
- Integration
- DevOps
- API
- Productivity
author: Community
featured: false
---

MCP сервер, который предоставляет инструменты для поиска, установки и проксирования других MCP серверов с расширенными возможностями поиска, включая векторный поиск по сходству и агрегацию результатов от нескольких провайдеров.

## Установка

### UVX (Рекомендуется)

```bash
export NACOS_ADDR=127.0.0.1:8848
export NACOS_USERNAME=nacos
export NACOS_PASSWORD=$PASSWORD
uvx nacos-mcp-router@latest
```

### PIP

```bash
pip install nacos-mcp-router
export NACOS_ADDR=127.0.0.1:8848
export NACOS_USERNAME=nacos
export NACOS_PASSWORD=$PASSWORD
python -m nacos_mcp_router
```

### Docker

```bash
docker run -i --rm --network host -e NACOS_ADDR=$NACOS_ADDR -e NACOS_USERNAME=$NACOS_USERNAME -e NACOS_PASSWORD=$NACOS_PASSWORD -e TRANSPORT_TYPE=$TRANSPORT_TYPE nacos/nacos-mcp-router:latest
```

### NPX (TypeScript)

```bash
npx nacos-mcp-router@latest
```

## Конфигурация

### Claude Desktop (UVX)

```json
{
    "mcpServers":
    {
        "nacos-mcp-router":
        {
            "command": "uvx",
            "args":
            [
                "nacos-mcp-router@latest"
            ],
            "env":
            {
                "NACOS_ADDR": "<NACOS-ADDR>, опционально, по умолчанию 127.0.0.1:8848",
                "NACOS_USERNAME": "<NACOS-USERNAME>, опционально, по умолчанию nacos",
                "NACOS_PASSWORD": "<NACOS-PASSWORD>, обязательно"
            }
        }
    }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "nacos-mcp-router": {
      "command": "docker",
      "args": [
        "run", "-i", "--rm", "--network", "host",  "-e", "NACOS_ADDR=<NACOS-ADDR>", "-e",  "NACOS_USERNAME=<NACOS-USERNAME>", "-e", "NACOS_PASSWORD=<NACOS-PASSWORD>" ,"-e", "TRANSPORT_TYPE=stdio", "nacos/nacos-mcp-router:latest"
      ]
    }
  }
}
```

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "nacos-mcp-router": {
      "command": "npx",
      "args": [
        "nacos-mcp-router@latest"
      ],
      "env": {
        "NACOS_ADDR": "<NACOS-ADDR>, опционально, по умолчанию 127.0.0.1:8848",
        "NACOS_USERNAME": "<NACOS-USERNAME>, опционально, по умолчанию nacos",
        "NACOS_PASSWORD": "<NACOS-PASSWORD>, обязательно"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `search_mcp_server` | Поиск MCP серверов по описанию задач и ключевым словам, возвращает список MCP серверов и инструкции |
| `add_mcp_server` | Добавление MCP сервера - устанавливает stdio серверы и устанавливает соединения, возвращает список инструментов и использ... |
| `use_tool` | Проксирование запросов к инструментам целевого MCP сервера, позволяя LLM использовать инструменты других MCP серверов |

## Возможности

- Режим роутера для рекомендации, распределения, установки и проксирования MCP серверов
- Режим прокси для конвертации SSE и stdio протокола MCP серверов в потоковый HTTP протокол
- Расширенные возможности поиска с векторным поиском по сходству и агрегацией результатов от нескольких провайдеров
- Nacos провайдер для обнаружения сервисов с сопоставлением ключевых слов и векторным поиском по сходству
- Compass провайдер для улучшенного семантического поиска и оценки релевантности
- Настраиваемое поведение поиска с порогами сходства и ограничениями результатов
- Поддержка нескольких транспортных протоколов (stdio, sse, streamable_http)

## Переменные окружения

### Обязательные
- `NACOS_PASSWORD` - пароль Nacos

### Опциональные
- `NACOS_ADDR` - адрес сервера Nacos
- `NACOS_USERNAME` - имя пользователя Nacos
- `COMPASS_API_BASE` - COMPASS API эндпоинт для улучшенного поиска
- `SEARCH_MIN_SIMILARITY` - минимальная оценка сходства для результатов (0.0 до 1.0)
- `SEARCH_RESULT_LIMIT` - максимальное количество результатов для возврата
- `NACOS_NAMESPACE` - пространство имен Nacos
- `TRANSPORT_TYPE` - тип транспортного протокола (stdio, sse, streamable_http)
- `PROXIED_MCP_NAME` - в режиме прокси, указывает имя MCP сервера для конвертации

## Примеры использования

```
Поиск MCP серверов для обработки естественного языка
```

```
Поиск MCP серверов по задачам и ключевым словам
```

```
Автоматическая установка и подключение к MCP серверам
```

```
Проксирование запросов к инструментам других MCP серверов
```

## Ресурсы

- [GitHub Repository](https://github.com/nacos-group/nacos-mcp-router)

## Примечания

Nacos-MCP-Router имеет два режима работы: режим роутера (по умолчанию) для управления MCP серверами, и режим прокси для конвертации протоколов. Сервер интегрируется с платформой обнаружения сервисов Nacos и обеспечивает улучшенный поиск через COMPASS API. Лицензирован под Apache 2.0.