---
title: Bybit MCP сервер
description: MCP сервер для криптовалютной биржи Bybit, который позволяет AI-ассистентам взаимодействовать с торговыми платформами для получения рыночных данных, управления аккаунтом и автоматической торговли.
tags:
- Finance
- API
- Analytics
- Integration
author: ethancod1ng
featured: false
---

MCP сервер для криптовалютной биржи Bybit, который позволяет AI-ассистентам взаимодействовать с торговыми платформами для получения рыночных данных, управления аккаунтом и автоматической торговли.

## Установка

### NPM Global

```bash
npm install -g bybit-mcp-server
```

### NPX

```bash
npx bybit-mcp-server
```

### Из исходников

```bash
git clone https://github.com/your-username/bybit-mcp-server.git
cd bybit-mcp-server
npm install
cp .env.example .env
npm run dev
```

## Конфигурация

### Claude Desktop (Testnet)

```json
{
  "mcpServers": {
    "bybit": {
      "command": "npx",
      "args": ["bybit-mcp-server"],
      "env": {
        "BYBIT_API_KEY": "your_testnet_api_key",
        "BYBIT_API_SECRET": "your_testnet_api_secret",
        "BYBIT_ENVIRONMENT": "testnet"
      }
    }
  }
}
```

### Claude Desktop (Mainnet)

```json
{
  "mcpServers": {
    "bybit": {
      "command": "npx",
      "args": ["bybit-mcp-server"],
      "env": {
        "BYBIT_API_KEY": "your_mainnet_api_key",
        "BYBIT_API_SECRET": "your_mainnet_api_secret",
        "BYBIT_ENVIRONMENT": "mainnet"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_price` | Получить текущую цену торгового символа |
| `get_orderbook` | Получить глубину стакана заявок для торгового символа |
| `get_klines` | Получить исторические данные свечей |
| `get_24hr_ticker` | Получить 24-часовую торговую статистику |
| `get_account_info` | Получить информацию об аккаунте и балансах |
| `get_wallet_balance` | Получить баланс кошелька для определенного типа аккаунта |
| `get_open_orders` | Получить список открытых/активных ордеров |
| `get_order_history` | Получить историю ордеров |
| `place_order` | Разместить новый ордер |
| `cancel_order` | Отменить существующий ордер |
| `cancel_all_orders` | Отменить все ордера для символа или категории |

## Возможности

- Доступ к рыночным данным криптовалют в реальном времени
- Управление балансом аккаунта и кошельком
- Размещение и отмена ордеров
- Получение исторических торговых данных
- Поддержка как testnet, так и mainnet окружений
- Автоматическое скрытие API ключей для безопасности
- Интеграция с Claude Desktop и Cursor

## Переменные окружения

### Обязательные
- `BYBIT_API_KEY` - Ваш API ключ Bybit
- `BYBIT_API_SECRET` - Ваш API секрет Bybit

### Опциональные
- `BYBIT_ENVIRONMENT` - Окружение для использования (testnet или mainnet)
- `BYBIT_BASE_URL` - Пользовательский базовый URL API
- `DEBUG` - Включить отладочное логирование

## Примеры использования

```
Получить текущую цену BTCUSDT на Bybit
```

```
Показать мне стакан заявок для ETHUSDT с 50 уровнями
```

```
Получить баланс моего аккаунта
```

```
Разместить лимитный ордер на покупку 0.1 BTC по цене $45000
```

```
Отменить все мои открытые ордера для BTCUSDT
```

## Ресурсы

- [GitHub Repository](https://github.com/ethancod1ng/bybit-mcp-server)

## Примечания

⚠️ ПРЕДУПРЕЖДЕНИЕ: Операции на mainnet используют реальные средства. Рекомендуется testnet для тестирования. Всегда тщательно тестируйте на testnet перед использованием mainnet. Реализует API эндпоинты Bybit V5. Многоязычная документация доступна на английском, китайском и японском языках.