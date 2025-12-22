---
title: ShareSeer MCP сервер
description: MCP сервер, который предоставляет доступ к обширной базе данных SEC документов, инсайдерских транзакций и финансовых данных ShareSeer через Claude и другие совместимые с MCP AI-ассистенты.
tags:
- Finance
- Analytics
- API
- Database
author: shareseer
featured: false
---

MCP сервер, который предоставляет доступ к обширной базе данных SEC документов, инсайдерских транзакций и финансовых данных ShareSeer через Claude и другие совместимые с MCP AI-ассистенты.

## Конфигурация

### Интеграция с Claude Desktop

```json
https://shareseer.com/mcp?api_key=YOUR_API_KEY_HERE
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_company_filings` | Получить последние SEC документы для конкретной компании |
| `get_insider_transactions` | Получить инсайдерские торговые транзакции для компании |
| `get_recent_filings` | Получить последние SEC документы по всем компаниям |
| `get_recent_insider_activity` | Получить недавнюю инсайдерскую торговую активность |
| `get_largest_daily_transactions` | Получить крупнейшие дневные инсайдерские транзакции |
| `get_largest_weekly_transactions` | Получить крупнейшие недельные инсайдерские транзакции |

## Возможности

- Доступ к SEC документам для конкретных компаний и всего рынка
- Данные по инсайдерским торговым транзакциям
- Отслеживание крупнейших дневных и недельных транзакций
- Бесплатный тариф с лимитами 10/час, 50/день
- Премиум тариф с лимитами 100/час, 1K/день и 10-летней историей данных
- Удаленное размещение MCP сервера (локальная установка не требуется)

## Переменные окружения

### Обязательные
- `API_KEY` - ShareSeer API ключ (начинается с sk-shareseer-), получается на странице профиля

## Примеры использования

```
Show me recent insider trading for Tesla
```

```
Who made the biggest stock purchases today?
```

```
What are the most recent 10-K filings?
```

```
Show me the largest insider selling activity this week
```

```
Show me the largest insider buying activity this week
```

## Ресурсы

- [GitHub Repository](https://github.com/shareseer/shareseer-mcp-server)

## Примечания

Требуется регистрация аккаунта ShareSeer на shareseer.com/signup. Использует удаленный MCP сервер (рекомендуется) - локальная установка не нужна. Бесплатный тариф ограничен 6 месяцами данных и 3 результатами для инсайдерских транзакций. Премиум тариф ($14.99/мес) включает 10-летнюю историю данных, неограниченные результаты и поддержку пагинации.