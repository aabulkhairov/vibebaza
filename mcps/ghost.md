---
title: Ghost MCP сервер
description: MCP сервер для взаимодействия с Ghost CMS через LLM интерфейсы вроде Claude, обеспечивающий безопасный и полный доступ к вашему Ghost блогу с JWT аутентификацией.
tags:
- CRM
- API
- Productivity
- Integration
- Analytics
author: MFYDev
featured: true
---

MCP сервер для взаимодействия с Ghost CMS через LLM интерфейсы вроде Claude, обеспечивающий безопасный и полный доступ к вашему Ghost блогу с JWT аутентификацией.

## Установка

### NPX

```bash
npx -y @fanyangmeng/ghost-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
      "ghost-mcp": {
        "command": "npx",
        "args": ["-y", "@fanyangmeng/ghost-mcp"],
        "env": {
            "GHOST_API_URL": "https://yourblog.com",
            "GHOST_ADMIN_API_KEY": "your_admin_api_key",
            "GHOST_API_VERSION": "v5.0"
        }
      }
    }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `browse_posts` | Список постов с опциональными фильтрами, пагинацией и сортировкой |
| `read_post` | Получение поста по ID или slug |
| `add_post` | Создание нового поста с заголовком, контентом и статусом |
| `edit_post` | Обновление существующего поста по ID |
| `delete_post` | Удаление поста по ID |
| `browse_members` | Список участников с фильтрами и пагинацией |
| `read_member` | Получение участника по ID или email |
| `add_member` | Создание нового участника |
| `edit_member` | Обновление данных участника |
| `delete_member` | Удаление участника |
| `browse_newsletters` | Список рассылок |
| `read_newsletter` | Получение рассылки по ID |
| `add_newsletter` | Создание новой рассылки |
| `edit_newsletter` | Обновление данных рассылки |
| `delete_newsletter` | Удаление рассылки |

## Возможности

- Безопасные запросы к Ghost Admin API с помощью @tryghost/admin-api
- Полный доступ к сущностям, включая посты, пользователей, участников, тарифы, предложения и рассылки
- Продвинутая функция поиска с опциями нечёткого и точного соответствия
- Подробный, читаемый вывод для Ghost сущностей
- Надёжная обработка ошибок с использованием пользовательских исключений GhostError
- Встроенная поддержка логирования через MCP контекст для улучшенного устранения неполадок

## Переменные окружения

### Обязательные
- `GHOST_API_URL` - URL вашего Ghost блога (например, https://yourblog.com)
- `GHOST_ADMIN_API_KEY` - Ваш Ghost admin API ключ для аутентификации
- `GHOST_API_VERSION` - Версия Ghost API для использования (например, v5.0)

## Ресурсы

- [GitHub Repository](https://github.com/MFYDev/ghost-mcp)

## Примечания

Это полная перезапись с Python на TypeScript в версии v0.1.0, которая принесла упрощённую установку через NPM пакет, улучшенную надёжность с официальным Ghost admin API клиентом и оптимизированную конфигурацию. Кардинальные изменения по сравнению с Python версией включают другой процесс установки и метод конфигурации.