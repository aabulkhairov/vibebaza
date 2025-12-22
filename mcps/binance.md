---
title: Binance MCP сервер
description: MCP сервер для торговли криптовалютой и получения рыночных данных через API биржи Binance.
tags:
- Finance
- API
- Analytics
- Integration
author: ethancod1ng
featured: false
install_command: claude mcp add binance --env BINANCE_API_KEY=YOUR_API_KEY --env BINANCE_API_SECRET=YOUR_API_SECRET
  --env BINANCE_TESTNET=false -- npx -y binance-mcp-server
---

MCP сервер для торговли криптовалютой и получения рыночных данных через API биржи Binance.

## Установка

### NPM Global

```bash
npm install -g binance-mcp-server
```

## Конфигурация

### MCP конфигурация

```json
{
  "mcpServers": {
    "binance": {
      "command": "npx",
      "args": ["binance-mcp-server"],
      "env": {
        "BINANCE_API_KEY": "your_api_key",
        "BINANCE_API_SECRET": "your_api_secret",
        "BINANCE_TESTNET": "false"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_price` | Получить текущую цену торговой пары |
| `get_orderbook` | Получить данные глубины книги заказов |
| `get_klines` | Получить данные K-линий/свечей |
| `get_24hr_ticker` | Получить 24-часовую статистику цен |
| `get_account_info` | Получить информацию об аккаунте и балансах |
| `get_open_orders` | Получить текущие открытые заказы |
| `get_order_history` | Получить историю заказов |
| `place_order` | Разместить новый заказ (поддерживает mainnet и testnet) |
| `cancel_order` | Отменить конкретный заказ (поддерживает mainnet и testnet) |
| `cancel_all_orders` | Отменить все открытые заказы (поддерживает mainnet и testnet) |

## Возможности

- Доступ к рыночным данным (цены, книги заказов, K-линии, 24-часовая статистика)
- Информация об аккаунте и проверка баланса
- Функциональность торговли (размещение, отмена и управление заказами)
- Поддержка testnet для безопасного тестирования с виртуальными средствами
- Многоязычная документация (английский, китайский, японский)
- Совместимость с Claude, Cursor и инструментами Trae AI

## Переменные окружения

### Обязательные
- `BINANCE_API_KEY` - Ваш API ключ Binance
- `BINANCE_API_SECRET` - Ваш API секрет Binance

### Опциональные
- `BINANCE_TESTNET` - Установите 'true' для testnet (виртуальные средства) или 'false' для mainnet (реальные деньги)

## Примеры использования

```
Get the current price of Bitcoin
```

```
Show me the order book for ETHUSDT
```

```
Check my account balance
```

```
Place a limit buy order for 0.001 BTC at $50,000
```

## Ресурсы

- [GitHub Repository](https://github.com/ethancod1ng/binance-mcp-server)

## Примечания

Установите BINANCE_TESTNET=true для безопасного тестирования с виртуальными средствами. Торговля на mainnet использует реальные деньги и показывает предупреждения перед выполнением заказов. API ключи можно получить из Binance Testnet (для разработки) или Binance mainnet (требует KYC верификацию).