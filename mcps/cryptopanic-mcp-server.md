---
title: cryptopanic-mcp-server MCP сервер
description: Предоставляет AI-агентам свежие новости криптовалют через CryptoPanic API.
tags:
- Finance
- API
- Media
- Analytics
author: kukapay
featured: false
---

Предоставляет AI-агентам свежие новости криптовалют через CryptoPanic API.

## Конфигурация

### Конфигурация MCP сервера

```json
"mcpServers": { 
  "cryptopanic-mcp-server": { 
    "command": "uv", 
    "args": [ 
      "--directory", 
      "/your/path/to/cryptopanic-mcp-server", 
      "run", 
      "main.py" 
    ], 
    "env": { 
      "CRYPTOPANIC_API_PLAN": "your_api_plan",
      "CRYPTOPANIC_API_KEY": "your_api_key" 
    } 
  } 
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `get_crypto_news` | Получает новости криптовалют с настраиваемым типом контента и пагинацией |

## Возможности

- Получение последних новостей криптовалют
- Поддержка различных типов контента (новости, медиа)
- Поддержка пагинации для загрузки нескольких страниц
- Интеграция с CryptoPanic API

## Переменные окружения

### Обязательные
- `CRYPTOPANIC_API_KEY` - API ключ из портала разработчиков CryptoPanic
- `CRYPTOPANIC_API_PLAN` - Тип API плана CryptoPanic

## Примеры использования

```
Get the latest cryptocurrency news
```

```
Fetch crypto media content
```

```
Retrieve multiple pages of cryptocurrency updates
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/cryptopanic-mcp-server)

## Примечания

Требуется API ключ и план CryptoPanic с сайта https://cryptopanic.com/developers/api/. За один запрос можно получить максимум 10 страниц.