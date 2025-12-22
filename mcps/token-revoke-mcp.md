---
title: token-revoke-mcp MCP сервер
description: MCP сервер для проверки и отзыва разрешений ERC-20 токенов в более чем 50 EVM-совместимых сетях, повышающий безопасность и контроль над одобрениями токенов.
tags:
- Security
- Finance
- API
- Integration
author: kukapay
featured: false
---

MCP сервер для проверки и отзыва разрешений ERC-20 токенов в более чем 50 EVM-совместимых сетях, повышающий безопасность и контроль над одобрениями токенов.

## Установка

### Из исходного кода

```bash
git clone https://github.com/kukapay/token-revoke-mcp.git
cd token-revoke-mcp
npm install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "token-revoke-mcp": {
      "command": "node",
      "args": ["path/to/token-revoke-mcp/index.js"],
      "env": {
        "MORALIS_API_KEY": "your moralis api key",
        "PRIVATE_KEY": "your wallet private key"
      }
    }
  }
}
```

## Возможности

- Получение одобрений токенов: Извлечение всех одобрений ERC20 токенов для кошелька в указанной сети, включая детали токенов, балансы и USD стоимость под риском
- Отзыв разрешений: Отправка транзакций для отзыва разрешений ERC20 токенов для конкретных получателей
- Проверка статуса транзакций: Верификация успеха или неудачи отправленных транзакций с использованием хешей транзакций
- Поддержка множества сетей: Поддерживает более 50 EVM-совместимых сетей, включая основные сети (например, Ethereum, Polygon, BSC) и тестовые сети (например, Goerli, Mumbai)

## Переменные окружения

### Обязательные
- `MORALIS_API_KEY` - Требуется для получения данных об одобрениях токенов из Moralis API
- `PRIVATE_KEY` - Ethereum-совместимый приватный ключ для подписи транзакций отзыва

## Примеры использования

```
Show me all the token approvals for my wallet on Polygon
```

```
Revoke the allowance for token 0x2791bca1f2de4661ed88a30c99a7a9449aa84174 to spender 0x1111111254eeb25477b68fb85ed929f73a960582 on BSC
```

```
Did my transaction 0x123... on BSC go through?
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/token-revoke-mcp)

## Примечания

Требует Node.js 18 или выше для поддержки нативного fetch. Поддерживает основные сети как Ethereum, Polygon, BSC, Avalanche, Fantom, Arbitrum, Optimism и тестовые сети как Goerli, Mumbai, BSC testnet, Arbitrum Goerli, Optimism Sepolia.