---
title: Paradex MCP сервер
description: MCP сервер для торговой платформы Paradex, который позволяет AI ассистентам получать рыночные данные, управлять торговыми аккаунтами и хранилищами, размещать и управлять ордерами, а также отслеживать позиции и баланс.
tags:
- Finance
- API
- Analytics
- Integration
author: sv
featured: false
install_command: claude mcp add paradex uvx mcp-paradex
---

MCP сервер для торговой платформы Paradex, который позволяет AI ассистентам получать рыночные данные, управлять торговыми аккаунтами и хранилищами, размещать и управлять ордерами, а также отслеживать позиции и баланс.

## Установка

### PyPI

```bash
pip install mcp-paradex
```

### uvx (Рекомендуется)

```bash
uvx mcp-paradex
```

### Smithery (Claude Desktop)

```bash
npx -y @smithery/cli install @sv/mcp-paradex-py --client claude
```

### Docker

```bash
# Сборка образа
docker build . -t sv/mcp-paradex-py

# Запуск (только публичные функции)
docker run --rm -i sv/mcp-paradex-py

# Запуск с возможностями торговли
docker run --rm -e PARADEX_ACCOUNT_PRIVATE_KEY=your_key -i sv/mcp-paradex-py
```

### Из исходного кода

```bash
git clone https://github.com/sv/mcp-paradex-py.git
cd mcp-paradex-py
uv sync --dev --all-extras
uv run mcp-paradex
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "paradex": {
      "command": "uvx",
      "args": ["mcp-paradex"],
      "env": {
        "PARADEX_ENVIRONMENT": "testnet",
        "PARADEX_ACCOUNT_PRIVATE_KEY": "your_private_key"
      }
    }
  }
}
```

### Paradex Documentation MCP

```json
"paradex-docs-mcp": {
   "command": "uvx",
   "args": [
      "--from",
      "mcpdoc",
      "mcpdoc",
      "--urls",
      "Paradex:https://docs.paradex.trade/llms.txt",
      "--transport",
      "stdio"
   ]
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `paradex_system_config` | Получить глобальную конфигурацию системы |
| `paradex_system_state` | Получить текущее состояние системы |
| `paradex_markets` | Получить детальную информацию о рынках |
| `paradex_market_summaries` | Получить сводки рынков с метриками |
| `paradex_funding_data` | Получить исторические данные о ставках фондирования |
| `paradex_orderbook` | Получить текущую книгу ордеров с настраиваемой глубиной |
| `paradex_klines` | Получить исторические данные свечей |
| `paradex_trades` | Получить недавние сделки |
| `paradex_bbo` | Получить лучшие предложения на покупку и продажу |
| `paradex_account_summary` | Получить сводку аккаунта |
| `paradex_account_positions` | Получить текущие позиции |
| `paradex_account_fills` | Получить исполненные сделки |
| `paradex_account_funding_payments` | Получить платежи по фондированию |
| `paradex_account_transactions` | Получить историю транзакций |
| `paradex_open_orders` | Получить все открытые ордера |

## Возможности

- Получение рыночных данных с Paradex
- Управление торговыми аккаунтами и хранилищами
- Размещение и управление ордерами
- Мониторинг позиций и баланса
- Доступ к конфигурации и состоянию системы
- Получение исторических данных свечей и ставок фондирования
- Доступ к книге ордеров и недавним сделкам
- Получение сводок аккаунта и истории транзакций
- Комплексный анализ позиций
- Оценка рисков портфеля

## Переменные окружения

### Обязательные
- `PARADEX_ENVIRONMENT` - Установить 'testnet' или 'mainnet'
- `PARADEX_ACCOUNT_PRIVATE_KEY` - Ваш приватный ключ аккаунта Paradex

## Примеры использования

```
market_overview - Комплексный обзор криптовалютного рынка
```

```
market_analysis - Детальный технический анализ и анализ микроструктуры
```

```
position_management - Комплексный анализ позиций
```

```
create_optimal_order - Разработка оптимальных параметров ордера
```

```
hedging_strategy - Разработка эффективных стратегий хеджирования
```

## Ресурсы

- [GitHub Repository](https://github.com/sv/mcp-paradex-py)

## Примечания

Требуется Python 3.10+. Расширенные результаты доступны с Paradex documentation MCP для дополнительного контекста. Поддерживает как testnet, так и mainnet окружения.