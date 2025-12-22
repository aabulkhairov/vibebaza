---
title: HDW LinkedIn MCP сервер
description: Инфраструктура для веб-скрапинга, ориентированная на агентов, которая предоставляет AI-агентам прямой доступ к данным в реальном времени из LinkedIn, Instagram, Reddit, Twitter и любых веб-сайтов через специализированные API с OAuth-аутентификацией.
tags:
- Web Scraping
- AI
- Search
- Analytics
- Integration
author: Community
featured: false
---

Инфраструктура для веб-скрапинга, ориентированная на агентов, которая предоставляет AI-агентам прямой доступ к данным в реальном времени из LinkedIn, Instagram, Reddit, Twitter и любых веб-сайтов через специализированные API с OAuth-аутентификацией.

## Установка

### Удаленный OAuth (Рекомендуется)

```bash
1. Sign up at app.anysite.io
2. Get OAuth URL: https://api.anysite.io/mcp/sse
3. Add to MCP client
```

### NPX

```bash
npx -y @anysite/mcp
```

### Из исходного кода

```bash
git clone https://github.com/anysiteio/anysite-mcp-server.git
cd anysite-mcp-server
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
1. Open Claude Desktop → Settings → Connectors
2. Click Add Custom Connector
3. Name: AnySite MCP
4. OAuth URL: https://api.anysite.io/mcp/sse
```

### Cline/Cursor/Windsurf

```json
{
  "mcpServers": {
    "anysite": {
      "command": "npx",
      "args": ["-y", "@anysite/mcp"],
      "env": {
        "ANYSITE_OAUTH_URL": "https://api.anysite.io/mcp/sse"
      }
    }
  }
}
```

### Локальный сервер

```json
{
  "mcpServers": {
    "anysite-local": {
      "command": "node",
      "args": ["/path/to/anysite-mcp-server/build/index.js"],
      "env": {
        "ANYSITE_ACCESS_TOKEN": "your_token",
        "ANYSITE_ACCOUNT_ID": "your_account_id"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search_linkedin_users` | Расширенный поиск пользователей с 10+ фильтрами |
| `get_linkedin_profile` | Полный профиль с опытом, образованием, навыками |
| `get_instagram_user` | Информация профиля, подписчики, количество постов |
| `search_reddit_posts` | Поиск с сортировкой, временными фильтрами и фильтрами по сабреддитам |
| `google_search` | Поиск Google с чистыми результатами |
| `parse_webpage` | Извлечение контента с 14+ опциями CSS-селекторов |
| `get_twitter_user` | Детали профиля |
| `search_twitter_posts` | Расширенный поиск твитов с 15+ фильтрами |
| `send_linkedin_chat_message` | Отправка личных сообщений |
| `send_linkedin_connection` | Отправка запросов на подключение |

## Возможности

- OAuth-аутентификация - Безопасное подключение в один клик для Claude Desktop и других MCP-клиентов
- Поддержка множества платформ - LinkedIn, Instagram, Reddit, Twitter и кастомный парсинг веб-страниц
- Дизайн, ориентированный на агентов - Создан специально для AI-агентов со структурированными форматами данных
- Самовосстанавливающиеся API - Автоматическое восстановление после изменений платформ и ограничений скорости
- Данные в реальном времени - Свежие данные без устаревших кешей
- Расширенный поиск и фильтрация - Поиск людей по должности, компании, местоположению, образованию, навыкам
- Массовое извлечение данных - Извлечение тысяч профилей, постов или комментариев за один запрос
- Анализ сетей - Картирование связей, подписчиков, паттернов вовлеченности
- Мониторинг контента - Отслеживание постов, комментариев, реакций в реальном времени
- Управление аккаунтом - Отправка сообщений, запросов на подключение, комментариев к постам

## Переменные окружения

### Обязательные
- `ANYSITE_ACCESS_TOKEN` - Ваш токен доступа AnySite с app.anysite.io/settings/api-keys
- `ANYSITE_ACCOUNT_ID` - Ваш ID аккаунта AnySite с app.anysite.io/settings/api-keys

### Опциональные
- `ANYSITE_OAUTH_URL` - OAuth URL для удаленного MCP-подключения

## Примеры использования

```
Find me 10 CTOs at AI companies in San Francisco
```

```
Get the latest 20 Instagram posts mentioning @yourbrand
```

```
Search Reddit for posts about "LLM agents" in the last week, sorted by top engagement
```

```
Find the LinkedIn profile of John Doe at Company X and get his recent posts
```

```
What MCP tools do you have access to?
```

## Ресурсы

- [GitHub Repository](https://github.com/horizondatawave/hdw-mcp-server)

## Примечания

Предлагает 57 инструментов на различных платформах. Поддерживает как удаленный OAuth (рекомендуется для продакшена), так и локальный деплой сервера. Бесплатный тариф включает 100 кредитов с доступом ко всем инструментам. Работает с Claude Desktop, Cline, Cursor, Windsurf и любыми MCP-совместимыми клиентами. Корпоративные возможности включают управление командой и аналитику использования.