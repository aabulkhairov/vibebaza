---
title: APIWeaver MCP сервер
description: FastMCP сервер, который динамически создаёт MCP серверы из конфигураций веб API, позволяя легко интегрировать любой REST API, GraphQL endpoint или веб-сервис в MCP-совместимые инструменты для AI-ассистентов.
tags:
- API
- Integration
- Web Scraping
- Productivity
- AI
author: GongRzhe
featured: false
---

FastMCP сервер, который динамически создаёт MCP серверы из конфигураций веб API, позволяя легко интегрировать любой REST API, GraphQL endpoint или веб-сервис в MCP-совместимые инструменты для AI-ассистентов.

## Установка

### Из исходного кода

```bash
# Clone or download this repository
cd ~/Desktop/APIWeaver

# Install dependencies
pip install -r requirements.txt
```

### Командная строка

```bash
# Default STDIO transport
apiweaver run

# Streamable HTTP transport (recommended for web deployments)
apiweaver run --transport streamable-http --host 127.0.0.1 --port 8000

# SSE transport (legacy compatibility)
apiweaver run --transport sse --host 127.0.0.1 --port 8000
```

### Разработка

```bash
# From the root of the repository
python -m apiweaver.cli run [OPTIONS]
```

## Конфигурация

### Claude Desktop (UVX)

```json
{
  "mcpServers": {
    "apiweaver": {
      "command": "uvx",
      "args": ["apiweaver", "run"]
    }
  }
}
```

### Claude Desktop (Streamable HTTP)

```json
{
  "mcpServers": {
    "apiweaver": {
      "command": "apiweaver",
      "args": ["run", "--transport", "streamable-http", "--host", "127.0.0.1", "--port", "8000"]
    }
  }
}
```

### Claude Desktop (STDIO)

```json
{
  "mcpServers": {
    "apiweaver": {
      "command": "apiweaver",
      "args": ["run"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `register_api` | Регистрирует новый API и создаёт инструменты для его endpoints |
| `list_apis` | Выводит список всех зарегистрированных API и их endpoints |
| `unregister_api` | Удаляет API и его инструменты |
| `test_api_connection` | Тестирует подключение к зарегистрированному API |
| `call_api` | Универсальный инструмент для вызова любого зарегистрированного API endpoint |
| `get_api_schema` | Получает информацию о схеме для API и endpoints |

## Возможности

- Динамическая регистрация API - Регистрируйте любой веб API во время выполнения
- Множественные методы аутентификации - Bearer токены, API ключи, Basic auth, OAuth2 и кастомные заголовки
- Все HTTP методы - Поддержка GET, POST, PUT, DELETE, PATCH и других
- Гибкие параметры - Query параметры, path параметры, заголовки и тела запросов
- Автоматическая генерация инструментов - Каждый API endpoint становится MCP инструментом
- Встроенное тестирование - Тестируйте API подключения перед их использованием
- Обработка ответов - Автоматический парсинг JSON с fallback на текст
- Множественные типы транспорта - Поддержка STDIO, SSE и Streamable HTTP транспорта

## Примеры использования

```
Register the OpenWeatherMap API to get current weather for cities
```

```
Connect to GitHub API to get user information and repository data
```

```
Test API connectivity before using registered endpoints
```

```
Call any registered API endpoint with the generic call_api tool
```

```
List all available APIs and their configured endpoints
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/APIWeaver)

## Примечания

Поддерживает три типа транспорта: STDIO (по умолчанию, лучше всего для локальных инструментов), SSE (для обратной совместимости) и Streamable HTTP (рекомендуется для веб-деплоев). Опции аутентификации включают Bearer токены, API ключи (в заголовке или query параметре), Basic auth и кастомные заголовки. Параметры могут размещаться в query строках, URL путях, заголовках или телах запросов. Предоставляет детальную обработку ошибок для недостающих параметров, HTTP ошибок, сбоев подключения и проблем с аутентификацией.