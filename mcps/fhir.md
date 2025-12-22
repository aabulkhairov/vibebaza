---
title: FHIR MCP сервер
description: MCP сервер, который обеспечивает бесшовную интеграцию с FHIR API, выступая в качестве моста между AI/LLM инструментами и медицинскими данными для поиска, получения и анализа клинической информации.
tags:
- API
- Integration
- Analytics
- Security
author: wso2
featured: false
---

MCP сервер, который обеспечивает бесшовную интеграцию с FHIR API, выступая в качестве моста между AI/LLM инструментами и медицинскими данными для поиска, получения и анализа клинической информации.

## Установка

### PyPI пакет

```bash
uvx fhir-mcp-server
```

### Из исходников

```bash
git clone <repository_url>
cd <repository_directory>
uv venv
source .venv/bin/activate
uv pip sync requirements.txt
uv run fhir-mcp-server
```

### Docker

```bash
docker pull wso2/fhir-mcp-server:latest
docker run --env-file .env -p 8000:8000 fhir-mcp-server
```

### Docker Compose

```bash
docker-compose up -d
```

## Конфигурация

### Claude Desktop - Streamable HTTP

```json
{
    "mcpServers": {
        "fhir": {
            "command": "npx",
            "args": [
                "-y",
                "mcp-remote",
                "http://localhost:8000/mcp"
            ]
        }
    }
}
```

### Claude Desktop - STDIO

```json
{
    "mcpServers": {
        "fhir": {
            "command": "uv",
            "args": [
                "--directory",
                "/path/to/fhir-mcp-server",
                "run",
                "fhir-mcp-server",
                "--transport",
                "stdio"
            ],
            "env": {
                "FHIR_SERVER_ACCESS_TOKEN": "Your FHIR Access Token"
            }
        }
    }
}
```

### VS Code - Streamable HTTP

```json
"mcp": {
    "servers": {
        "fhir": {
            "type": "http",
            "url": "http://localhost:8000/mcp",
        }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_capabilities` | Получает метаданные о конкретном FHIR сервере |

## Возможности

- MCP-совместимый транспорт через stdio, SSE или streamable HTTP
- Поддержка SMART-on-FHIR аутентификации для безопасного подключения к FHIR серверам
- Интеграция инструментов с VS Code, Claude Desktop и MCP Inspector
- Поддержка OAuth 2.0 Authorization Code Grant flow
- Интеграция с экосистемой Epic EHR и HAPI FHIR серверами

## Переменные окружения

### Обязательные
- `FHIR_SERVER_BASE_URL` - Базовый URL FHIR сервера

### Опциональные
- `FHIR_SERVER_CLIENT_ID` - OAuth2 client ID, используемый для авторизации MCP клиентов с FHIR сервером
- `FHIR_SERVER_CLIENT_SECRET` - Секрет клиента, соответствующий FHIR client ID
- `FHIR_SERVER_SCOPES` - Список OAuth2 scope через пробел для запроса у FHIR сервера авторизации
- `FHIR_SERVER_DISABLE_AUTHORIZATION` - Если установлено в True, отключает проверки авторизации на MCP сервере
- `FHIR_MCP_HOST` - Имя хоста или IP адрес, к которому должен привязываться MCP сервер
- `FHIR_MCP_PORT` - Порт, на котором MCP сервер будет прослушивать входящие запросы клиентов
- `FHIR_SERVER_ACCESS_TOKEN` - Токен доступа для аутентификации запросов к FHIR серверу

## Ресурсы

- [GitHub Repository](https://github.com/wso2/fhir-mcp-server)

## Примечания

Поддерживает Python 3.8+, требует uv для управления зависимостями. При локальном запуске через Docker авторизация должна быть отключена установкой FHIR_SERVER_DISABLE_AUTHORIZATION=True. Включает демо интеграции с HAPI FHIR сервером и Epic Sandbox.