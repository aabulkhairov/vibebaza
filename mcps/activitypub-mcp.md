---
title: ActivityPub MCP сервер
description: MCP сервер для изучения и взаимодействия с Fediverse через протокол ActivityPub.
  Поддерживает поиск акторов, получение таймлайнов, исследование инстансов и WebFinger
  резолвинг по децентрализованным социальным сетям.
tags:
- API
- Integration
- Web Scraping
- Search
- Messaging
author: cameronrye
featured: false
---

MCP сервер для изучения и взаимодействия с Fediverse через протокол ActivityPub. Поддерживает поиск акторов, получение таймлайнов, исследование инстансов и WebFinger резолвинг по децентрализованным социальным сетям.

## Установка

### NPX

```bash
npx activitypub-mcp install
```

### Из исходников

```bash
git clone https://github.com/cameronrye/activitypub-mcp.git
cd activitypub-mcp
npm install
npm run setup
```

### Windows PowerShell

```bash
git clone https://github.com/cameronrye/activitypub-mcp.git
cd activitypub-mcp
npm run setup:windows
```

### macOS/Linux

```bash
git clone https://github.com/cameronrye/activitypub-mcp.git
cd activitypub-mcp
npm run setup:unix
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "activitypub": {
      "command": "npx",
      "args": ["-y", "activitypub-mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `discover-actor` | Найти и получить информацию о любом акторе в fediverse |
| `fetch-timeline` | Получить последние посты из таймлайна любого актора |
| `get-instance-info` | Получить детальную информацию о любом инстансе fediverse |
| `search-instance` | Искать контент на конкретном инстансе fediverse |
| `discover-instances` | Найти популярные инстансы fediverse по категории или теме |
| `recommend-instances` | Получить персонализированные рекомендации инстансов по интересам |
| `health-check` | Проверить статус работоспособности MCP сервера |
| `performance-metrics` | Получить метрики производительности MCP сервера |

## Возможности

- Fediverse клиент — взаимодействие с ActivityPub серверами (Mastodon, Pleroma, Misskey и др.)
- WebFinger Discovery — поиск и обнаружение акторов по всему fediverse
- Обнаружение удалённых акторов — поиск пользователей на любом инстансе fediverse
- Получение таймлайнов — посты из таймлайна любого пользователя
- Обнаружение инстансов — поиск и исследование инстансов fediverse
- Поисковые возможности — поиск контента по инстансам
- Мультиплатформенная поддержка — работает с Mastodon, Pleroma, Misskey и другими
- Списки подписчиков/подписок — доступ к социальным связям
- Кроссплатформенная совместимость — поддержка Windows, macOS и Linux

## Переменные окружения

### Опциональные
- `MCP_SERVER_NAME` — название конфигурации MCP сервера
- `MCP_SERVER_VERSION` — версия MCP сервера
- `RATE_LIMIT_ENABLED` — включить ограничение частоты запросов
- `RATE_LIMIT_MAX` — максимальное количество запросов
- `RATE_LIMIT_WINDOW` — окно ограничения в миллисекундах
- `LOG_LEVEL` — уровень логирования

## Примеры использования

```
Find information about a user on Mastodon
```

```
Get recent posts from a specific fediverse account
```

```
Discover popular instances in a particular category
```

```
Search for content about artificial intelligence across the fediverse
```

```
Get recommendations for technology-focused instances
```

## Ресурсы

- [GitHub Repository](https://github.com/cameronrye/activitypub-mcp)

## Примечания

Это read-only клиент для fediverse, не требующий аутентификации или создания аккаунта. Работает через исследование существующего публичного ActivityPub контента по децентрализованной социальной сети. Сервер включает исчерпывающую документацию, кроссплатформенные скрипты установки и встроенный мониторинг производительности.
