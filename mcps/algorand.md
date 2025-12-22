---
title: Algorand MCP сервер
description: Комплексный MCP сервер с 125+ инструментами и ресурсами для полного взаимодействия
  с блокчейном Algorand. Управление транзакциями, операции с кошельками, DeFi интеграции
  и доступ к обширной документации блокчейна.
tags:
- Finance
- API
- Analytics
- Integration
- Code
author: GoPlausible
featured: false
---

Комплексный MCP сервер с 125+ инструментами и ресурсами для полного взаимодействия с блокчейном Algorand. Управление транзакциями, операции с кошельками, DeFi интеграции и доступ к обширной документации блокчейна.

## Установка

### Из исходников

```bash
mkdir PATH_ON_YOUR_MACHINE/Claude/mcp-servers
cd PATH_ON_YOUR_MACHINE/Claude/mcp-servers
git clone https://github.com/GoPlausible/algorand-mcp.git
cd algorand-mcp
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "algorand-mcp": {
      "command": "node",
      "args": [
        "PATH_ON_YOUR_MACHINE/Claude/mcp-servers/algorand-mcp/packages/server/dist/index.js"
     ],
      "env": {
        "ALGORAND_NETWORK": "testnet",
        "ALGORAND_ALGOD_API": "https://testnet-api.algonode.cloud/v2",
        "ALGORAND_ALGOD": "https://testnet-api.algonode.cloud",
        "ALGORAND_INDEXER_API": "https://testnet-idx.algonode.cloud/v2",
        "ALGORAND_INDEXER": "https://testnet-idx.algonode.cloud",
        "ALGORAND_ALGOD_PORT": "",
        "ALGORAND_INDEXER_PORT": "",
        "ALGORAND_TOKEN": "",
        "ALGORAND_AGENT_WALLET": "problem aim online jaguar upper oil flight stumble mystery aerobic toy avoid file tomato moment exclude witness guard lab opera crunch noodle dune abandon broccoli",
        "NFD_API_URL": "https://api.nf.domains",
        "NFD_API_KEY": "",
        "TINYMAN_ACTIVE": "false",
        "ULTRADE_ACTIVE": "false",
        "VESTIGE_ACTIVE": "false",
        "ULTRADE_API_URL": "https://api.ultrade.io",
        "VESTIGE_API_URL": "https://api.vestigelabs.org",
        "VESTIGE_API_KEY": "",
        "ITEMS_PER_PAGE": "10"
      }
    }
  }
}
```

### macOS Claude Desktop

```json
{
  "mcpServers": {
    "algorand-mcp": {
      "command": "node",
      "args": [
        " /Users/YOUR_USERNAME/Library/Application\ Support/Claude/mcp-servers/algorand-mcp/packages/server/dist/index.js"
     ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `api_algod_get_account_info` | Получить текущий баланс аккаунта, ассеты и auth address |
| `api_algod_get_application_by_id` | Получить информацию о приложении |
| `api_algod_get_asset_by_id` | Получить текущую информацию об ассете |
| `api_indexer_search_for_accounts` | Поиск аккаунтов по разным критериям |
| `api_indexer_search_for_transactions` | Поиск транзакций |
| `api_nfd_get_nfd` | Получить NFD по имени или application ID |
| `api_vestige_view_assets` | Получить данные об ассетах |
| `api_tinyman_get_swap_quote` | Получить котировку для обмена ассетов |

## Возможности

- Полная интеграция документации Algorand с полной таксономией знаний
- Комплексный доступ к документации разработчика
- Документация ARCs, SDKs и инструментов
- Полные возможности взаимодействия с блокчейном Algorand
- Обширная система управления кошельками
- Комплексная обработка транзакций
- Богатые запросы состояния блокчейна
- Встроенные функции безопасности
- Интеграция NFDomains
- Vestige DeFi аналитика (опционально)

## Переменные окружения

### Обязательные
- `ALGORAND_NETWORK` — сеть для использования (testnet/mainnet)
- `ALGORAND_ALGOD_API` — URL эндпоинта Algod API
- `ALGORAND_INDEXER_API` — URL эндпоинта Indexer API
- `ALGORAND_AGENT_WALLET` — мнемоническая фраза для кошелька агента

### Опциональные
- `NFD_API_URL` — URL NFDomains API
- `NFD_API_KEY` — API ключ NFDomains
- `TINYMAN_ACTIVE` — включить интеграцию Tinyman AMM
- `ULTRADE_ACTIVE` — включить интеграцию Ultrade DEX
- `VESTIGE_ACTIVE` — включить интеграцию Vestige DeFi аналитики
- `ITEMS_PER_PAGE` — количество элементов на странице для пагинации

## Ресурсы

- [GitHub Repository](https://github.com/GoPlausible/algorand-mcp)

## Примечания

Требуется Node.js v23.6.1 или выше и npm v10.2.4 или выше. Проект включает готовый к продакшену серверный пакет и клиентский пакет в разработке для управления кошельками. Все ответы следуют стандартизированному формату со встроенной поддержкой пагинации. Сервер предоставляет доступ к комплексной таксономии документации Algorand через knowledge ресурсы.
