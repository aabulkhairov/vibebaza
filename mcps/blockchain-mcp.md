---
title: Blockchain MCP сервер
description: MCP сервер, который предоставляет доступ к Tatum Blockchain Data API и RPC Gateway, позволяя любым LLM читать и записывать блокчейн данные в более чем 130 сетях.
tags:
- API
- Finance
- Database
- Analytics
- Integration
author: tatumio
featured: false
---

MCP сервер, который предоставляет доступ к Tatum Blockchain Data API и RPC Gateway, позволяя любым LLM читать и записывать блокчейн данные в более чем 130 сетях.

## Установка

### NPM Global

```bash
npm install -g @tatumio/blockchain-mcp
```

### NPM Local

```bash
npm install @tatumio/blockchain-mcp
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "tatumio": {
      "command": "npx",
      "args": [
        "@tatumio/blockchain-mcp"
      ],
      "env": {
        "TATUM_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_metadata` | Получение метаданных NFT/мультитокенов по адресу и ID |
| `get_wallet_balance_by_time` | Получение баланса кошелька на определенное время |
| `get_wallet_portfolio` | Получение полного портфолио кошелька |
| `get_owners` | Получение владельцев NFT/токена |
| `check_owner` | Проверка владения адресом конкретного токена |
| `get_transaction_history` | Получение истории транзакций для адреса |
| `get_block_by_time` | Получение информации о блоке по временной метке |
| `get_tokens` | Получение токенов для конкретного кошелька |
| `check_malicous_address` | Проверка адреса на вредоносность |
| `get_exchange_rate` | Получение курсов обмена в реальном времени |
| `gateway_get_supported_chains` | Получение всех поддерживаемых блокчейн сетей |
| `gateway_get_supported_methods` | Получение поддерживаемых RPC методов для сети |
| `gateway_execute_rpc` | Выполнение RPC вызовов в любой поддерживаемой сети |

## Возможности

- 130+ блокчейн сетей: Bitcoin, Ethereum, Solana, Polygon, Arbitrum, Base, Avalanche и многие другие
- Blockchain Data API: блоки, транзакции, балансы, информация о сети и многое другое
- RPC Gateway: прямой доступ к блокчейн RPC endpoints
- EVM-совместимые сети (69 сетей): Ethereum, Layer 2, сайдчейны, корпоративные, игровые
- Non-EVM сети (61 сеть): Bitcoin, альтернативные монеты, платформы смарт-контрактов, корпоративные

## Переменные окружения

### Обязательные
- `TATUM_API_KEY` - API ключ из Tatum Dashboard для доступа к блокчейн данным

## Ресурсы

- [GitHub Repository](https://github.com/tatumio/blockchain-mcp)

## Примечания

Получите свой бесплатный API ключ в Tatum Dashboard по адресу https://dashboard.tatum.io. Посетите официальную страницу MCP на https://tatum.io/mcp для получения дополнительной информации.