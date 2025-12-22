---
title: whale-tracker-mcp MCP сервер
description: MCP сервер для отслеживания транзакций криптовалютных китов через Whale Alert API, обеспечивающий мониторинг и анализ крупных криптовалютных транзакций в реальном времени.
tags:
- Finance
- API
- Analytics
- Monitoring
author: Community
featured: false
---

MCP сервер для отслеживания транзакций криптовалютных китов через Whale Alert API, обеспечивающий мониторинг и анализ крупных криптовалютных транзакций в реальном времени.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @kukapay/whale-tracker-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/kukapay/whale-tracker-mcp.git
cd whale-tracker-mcp
uv add "mcp[cli]" httpx python-dotenv
```

### Альтернативная установка через pip

```bash
pip install mcp httpx python-dotenv
```

### Установка через MCP CLI

```bash
mcp install whale_tracker.py --name "WhaleTracker" -f .env
```

### Режим разработки

```bash
mcp dev whale_tracker.py --with-editable .
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_recent_transactions` | Получение последних транзакций китов с опциональными фильтрами по блокчейну, минимальной сумме и лимиту |
| `get_transaction_details` | Получение детальной информации о конкретной транзакции по её ID |

## Возможности

- Отслеживание и анализ крупных криптовалютных транзакций в реальном времени
- Ресурсы: whale://transactions/{blockchain} - Предоставляет последние транзакции для указанного блокчейна как контекстные данные
- Промпты: query_whale_activity - Переиспользуемый шаблон для анализа паттернов транзакций китов, с опциональной фильтрацией по блокчейну
- Асинхронные API вызовы через httpx для эффективных неблокирующих запросов
- Поддержка переменных окружения для безопасного управления API ключами

## Переменные окружения

### Обязательные
- `WHALE_ALERT_API_KEY` - API ключ для доступа к Whale Alert API для отслеживания транзакций криптовалютных китов

## Примеры использования

```
Покажи мне последние транзакции китов на Bitcoin
```

```
Какие последние транзакции китов на Ethereum с минимальной суммой $1,000,000?
```

```
Получи детали транзакции ID 123456789
```

```
Расскажи мне о транзакции ID 123456789
```

```
Проанализируй активность китов на Ethereum
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/whale-tracker-mcp)

## Примечания

Требует Python 3.10 или выше и API ключ Whale Alert с whale-alert.io. Совместим с MCP клиентами, такими как Claude Desktop и MCP Inspector. Сервер предоставляет инструменты, ресурсы и промпты для комплексного анализа транзакций китов.