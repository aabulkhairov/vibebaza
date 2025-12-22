---
title: gx-mcp-server MCP сервер
description: Предоставляет инструменты для валидации качества данных Great Expectations через MCP, позволяя AI агентам загружать датасеты, определять правила валидации и программно выполнять проверки качества данных.
tags:
- Analytics
- Database
- AI
- Monitoring
- Integration
author: Community
featured: false
install_command: claude mcp add gx-mcp-server-local -- uv run python -m gx_mcp_server
---

Предоставляет инструменты для валидации качества данных Great Expectations через MCP, позволяя AI агентам загружать датасеты, определять правила валидации и программно выполнять проверки качества данных.

## Установка

### Docker (Рекомендуется)

```bash
docker run -d -p 8000:8000 --name gx-mcp-server davidf9999/gx-mcp-server:latest
```

### Из исходного кода

```bash
git clone https://github.com/davidf9999/gx-mcp-server && cd gx-mcp-server
just install
```

### PyPI

```bash
uv pip install gx-mcp-server
```

### С поддержкой Snowflake

```bash
uv pip install -e .[snowflake]
```

### С поддержкой BigQuery

```bash
uv pip install -e .[bigquery]
```

## Конфигурация

### Режим STDIO

```json
{
  "mcpServers": {
    "gx-mcp-server": {
      "type": "stdio",
      "command": "uv",
      "args": ["run", "python", "-m", "gx_mcp_server"]
    }
  }
}
```

### Режим HTTP с аутентификацией

```json
{
  "mcpServers": {
    "gx-mcp-server": {
      "type": "http",
      "url": "https://your-server.com:8000/mcp/",
      "headers": {
        "Authorization": "Basic dXNlcjpwYXNz"
      }
    }
  }
}
```

## Возможности

- Загрузка CSV данных из файла, URL или встроенно (до 1 GB, настраивается)
- Загрузка таблиц из Snowflake или BigQuery с использованием URI префиксов
- Определение и изменение ExpectationSuites
- Валидация данных и получение детальных результатов (синхронно или асинхронно)
- Выбор хранилища в памяти (по умолчанию) или SQLite для датасетов и результатов
- Опциональная аутентификация Basic или Bearer токен для HTTP клиентов
- Настройка ограничения HTTP запросов в минуту
- Ограничение источников через конфигурацию allowed-origins
- Метрики Prometheus на настраиваемом порту метрик
- Трассировка OpenTelemetry через OTLP экспортер

## Переменные окружения

### Опциональные
- `MCP_SERVER_USER` - Имя пользователя для базовой аутентификации
- `MCP_SERVER_PASSWORD` - Пароль для базовой аутентификации
- `MCP_CSV_SIZE_LIMIT_MB` - Лимит размера CSV файла в MB (1-1024, по умолчанию 50)
- `GX_ANALYTICS_ENABLED` - Отключить анонимную передачу данных использования Great Expectations (установить в false)
- `MCP_SERVER_URL` - URL сервера для кастомных клиентов
- `MCP_AUTH_TOKEN` - Токен аутентификации для кастомных клиентов

## Примеры использования

```
Загрузить CSV данные id,age\n1,25\n2,19\n3,45 и валидировать возрасты 21-65, показать неудачные записи
```

## Ресурсы

- [GitHub Repository](https://github.com/davidf9999/gx-mcp-server)

## Примечания

Поддерживает как STDIO, так и HTTP режимы транспорта. HTTP режим включает опции аутентификации (Basic и Bearer JWT), ограничение скорости, контроль CORS и health эндпоинты. Может запускаться с Docker для простого деплоя. Включает коннекторы для хранилищ Snowflake и BigQuery со специальными URI префиксами. Предоставляет метрики Prometheus и трассировку OpenTelemetry для мониторинга в продакшене.