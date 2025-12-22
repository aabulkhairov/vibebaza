---
title: Telegram-mcp-server MCP сервер
description: Мощный MCP сервер, который позволяет Claude взаимодействовать с Telegram каналами
  и группами через веб-скрапинг и прямой доступ к API, обеспечивая в 100 раз более быструю
  производительность с неограниченным извлечением постов.
tags:
- Messaging
- Web Scraping
- API
- Search
- Integration
author: DLHellMe
featured: false
---

Мощный MCP сервер, который позволяет Claude взаимодействовать с Telegram каналами и группами через веб-скрапинг и прямой доступ к API, обеспечивая в 100 раз более быструю производительность с неограниченным извлечением постов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/DLHellMe/telegram-mcp-server.git
cd telegram-mcp-server
npm install
cp .env.example .env
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "telegram-scraper": {
      "command": "node",
      "args": ["/absolute/path/to/telegram-mcp-server/dist/index.js"],
      "env": {
        "TELEGRAM_API_ID": "your_api_id",
        "TELEGRAM_API_HASH": "your_api_hash"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `telegram_api_login` | Аутентификация через Telegram API (только при первом использовании) |
| `api_scrape_channel` | Извлечение постов из каналов с неограниченным получением по умолчанию |
| `api_search_channel` | Поиск в канале по ключевым словам |
| `scrape_channel` | Извлечение из публичных каналов через веб-скрапинг |
| `telegram_login` | Вход для доступа к ограниченному контенту через веб-скрапинг |

## Возможности

- Двухрежимная работа: режим API (в 100 раз быстрее) и режим веб-скрапинга
- Прямой доступ через протокол MTProto от Telegram
- Функциональность поиска внутри каналов
- Доступ к приватным каналам, участником которых вы являетесь
- Полные метаданные сообщений (просмотры, реакции, пересылки)
- Постоянные сессии - аутентификация один раз
- Неограниченное извлечение постов по умолчанию
- Скрапинг на основе браузера с Puppeteer
- Извлечение визуальных медиа

## Переменные окружения

### Опциональные
- `TELEGRAM_API_ID` - Ваш Telegram API ID с my.telegram.org
- `TELEGRAM_API_HASH` - Ваш Telegram API hash с my.telegram.org
- `TELEGRAM_DATA_PATH` - Переопределение директории хранения данных по умолчанию
- `BROWSER_TIMEOUT` - Таймаут браузера для режима веб-скрапинга

## Примеры использования

```
Use telegram_api_login to connect to Telegram
```

```
Use api_scrape_channel with url="https://t.me/channelname"
```

```
Use api_scrape_channel with url="https://t.me/channelname" and max_posts=50
```

```
Use api_search_channel with url="https://t.me/channelname" and query="keyword"
```

```
Use scrape_channel with url="https://t.me/channelname"
```

## Ресурсы

- [GitHub Repository](https://github.com/DLHellMe/telegram-mcp-server)

## Примечания

Требует Node.js 18.0.0+, Chrome/Chromium для веб-скрапинга и учетные данные Telegram API для режима API. Данные сессий хранятся безопасно в специфичных для платформы директориях. Никогда не коммитьте .env файлы с учетными данными API.