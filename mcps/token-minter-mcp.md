---
title: token-minter-mcp MCP сервер
description: MCP сервер, предоставляющий инструменты для AI агентов по созданию ERC-20 токенов с поддержкой 21 блокчейна, включая Ethereum, Polygon, Arbitrum и другие.
tags:
- Finance
- API
- Integration
author: kukapay
featured: false
---

MCP сервер, предоставляющий инструменты для AI агентов по созданию ERC-20 токенов с поддержкой 21 блокчейна, включая Ethereum, Polygon, Arbitrum и другие.

## Установка

### Из исходного кода

```bash
git clone https://github.com/kukapay/token-minter-mcp.git
cd token-minter-mcp/server
npm install
```

## Конфигурация

### Конфигурация MCP сервера

```json
{
  "mcpServers": {
    "Token-Minter-MCP": {
      "command": "node",
      "args": ["path/to/token-minter-mcp/server/index.js"],
      "env": {
        "INFURA_KEY": "your infura key",
        "PRIVATE_KEY": "your private key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `deployToken` | Развертывает новый ERC-20 токен (name, symbol, initialSupply, decimals, chainId) |
| `transferToken` | Переводит ERC-20 токены (tokenAddress, toAddress, amount, chainId) |
| `getTransactionInfo` | Получает детали транзакции (txHash, chainId) |
| `getTokenBalance` | Запрашивает баланс конкретного ERC-20 токена для текущего аккаунта |
| `getTokenInfo` | Запрашивает метаданные ERC-20 токена (tokenAddress, chainId) |
| `getBalance` | Проверяет баланс нативного токена (chainId) |

## Возможности

- Деплой новых ERC-20 токенов с настраиваемыми параметрами
- Запрос метаданных токена (название, символ, десятичные знаки, общее предложение)
- Инициация переводов токенов (возвращает хеш транзакции без подтверждения)
- Получение деталей транзакции по хешу
- Проверка баланса нативного токена текущего аккаунта
- Доступ к метаданным токена через URI
- Интерактивные подсказки для руководства по деплою
- Поддержка 21 блокчейна, включая Ethereum, Polygon, Arbitrum, Base и другие

## Переменные окружения

### Обязательные
- `INFURA_KEY` - Валидный API ключ Infura для доступа к EVM сетям
- `PRIVATE_KEY` - Ethereum приватный ключ для подписания транзакций

## Примеры использования

```
I want to create a new token called 'RewardToken' with the symbol 'RWD' on Arbitrum. It should have 5 million tokens in initial supply and use 6 decimal places.
```

```
Can you tell me how much POL I have in my wallet on the Polygon network?
```

```
What's the balance of my newly created token on Polygon?
```

```
Please transfer 150.75 USDC from my account to 0xRecipientAddressHere on Polygon.
```

```
What's the status of my token deployment transaction with hash 0xabc123... on Arbitrum?
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/token-minter-mcp)

## Примечания

Поддерживает 21 сеть, включая Ethereum, Polygon, BSC, Arbitrum, Optimism, Linea, Base, Blast, Palm, Avalanche, Celo, zkSync, Mantle, opBNB, Scroll, Swellchain, Unichain, Starknet, Berachain, Hyperliquid и Sonic. Для локального тестирования используйте chainId 1337 с Hardhat нодой. Включает значок оценки безопасности от MseeP.ai.