---
title: AWS S3 MCP сервер
description: Реализация MCP сервера для извлечения данных, таких как PDF-файлы, из AWS S3 бакетов, обеспечивающая доступ к объектам S3 через ресурсы и инструменты.
tags:
- Cloud
- Storage
- API
- Integration
- Productivity
author: aws-samples
featured: false
---

Реализация MCP сервера для извлечения данных, таких как PDF-файлы, из AWS S3 бакетов, обеспечивающая доступ к объектам S3 через ресурсы и инструменты.

## Установка

### Разработка/Неопубликованная версия

```bash
uv --directory /Users/user/generative_ai/model_context_protocol/s3-mcp-server run s3-mcp-server
```

### Опубликованная версия

```bash
uvx s3-mcp-server
```

### Сборка из исходного кода

```bash
uv sync
uv build
uv publish
```

## Конфигурация

### Claude Desktop - Разработка

```json
{
  "mcpServers": {
    "s3-mcp-server": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/user/generative_ai/model_context_protocol/s3-mcp-server",
        "run",
        "s3-mcp-server"
      ]
    }
  }
}
```

### Claude Desktop - Опубликованная версия

```json
{
  "mcpServers": {
    "s3-mcp-server": {
      "command": "uvx",
      "args": [
        "s3-mcp-server"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `ListBuckets` | Возвращает список всех бакетов, принадлежащих аутентифицированному отправителю запроса |
| `ListObjectsV2` | Возвращает некоторые или все (до 1000) объекты в бакете с каждым запросом |
| `GetObject` | Извлекает объект из Amazon S3. В запросе GetObject укажите полное имя ключа для о... |

## Возможности

- Предоставление данных AWS S3 через ресурсы (как GET эндпоинты для загрузки информации в контекст LLM)
- Поддержка PDF документов (в настоящее время единственный поддерживаемый формат)
- Ограничение до 1000 объектов на запрос
- Поддержка запросов как в virtual-hosted-style, так и в path-style
- Интеграция с AWS S3 бакетами

## Переменные окружения

### Опциональные
- `UV_PUBLISH_TOKEN` - PyPI токен для публикации пакетов
- `UV_PUBLISH_USERNAME` - PyPI имя пользователя для публикации пакетов
- `UV_PUBLISH_PASSWORD` - PyPI пароль для публикации пакетов

## Ресурсы

- [GitHub репозиторий](https://github.com/aws-samples/sample-mcp-server-s3)

## Примечания

Требуются настроенные учетные данные AWS с использованием профиля по умолчанию с соответствующими разрешениями READ/WRITE для S3. Для отладки используйте MCP Inspector с: npx @modelcontextprotocol/inspector uv --directory /Users/user/generative_ai/model_context_protocol/s3-mcp-server run s3-mcp-server. Лицензирован под MIT-0 License.