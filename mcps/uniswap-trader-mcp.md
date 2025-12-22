---
title: uniswap-trader-mcp сервер
description: MCP сервер, который позволяет AI агентам автоматизировать обмен токенов на Uniswap DEX через множество блокчейнов, включая Ethereum, Optimism, Polygon, Arbitrum и другие.
tags:
- Finance
- API
- Integration
- Analytics
- Productivity
author: kukapay
featured: false
---

MCP сервер, который позволяет AI агентам автоматизировать обмен токенов на Uniswap DEX через множество блокчейнов, включая Ethereum, Optimism, Polygon, Arbitrum и другие.

## Установка

### NPX через Smithery

```bash
npx -y @smithery/cli install @kukapay/uniswap-trader-mcp --client claude
```

### Из исходного кода

```bash
git clone https://github.com/kukapay/uniswap-trader-mcp.git
cd uniswap-trader-mcp
npm install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Uniswap-Trader-MCP": {
      "command": "node",
      "args": ["path/to/uniswap-trader-mcp/server/index.js"],
      "env": {
        "INFURA_KEY": "your infura key",
        "WALLET_PRIVATE_KEY": "your private key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `getPrice` | Получает котировку в реальном времени для обмена на Uniswap с оптимизацией многоэтапного маршрута |
| `executeSwap` | Выполняет обмен токенов на Uniswap V3 с настраиваемым допуском проскальзывания и дедлайнами |

## Возможности

- Котировки в реальном времени для обмена токенов с оптимизацией многоэтапного маршрута
- Выполнение обменов на Uniswap V3 с настраиваемым допуском проскальзывания и дедлайнами
- Генерация торговых рекомендаций на основе ликвидности, комиссий и оптимальных путей
- Мультичейн поддержка для Ethereum, Optimism, Polygon, Arbitrum, Celo, BNB Chain, Avalanche и Base

## Переменные окружения

### Обязательные
- `INFURA_KEY` - API ключ Infura для доступа к блокчейн RPC
- `WALLET_PRIVATE_KEY` - Приватный ключ кошелька с средствами для выполнения обменов

## Примеры использования

```
Get me a price quote for swapping 1 ETH to DAI on Ethereum
```

```
Swap 1 ETH for DAI on Ethereum with a 0.5% slippage tolerance and a 20-minute deadline
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/uniswap-trader-mcp)

## Примечания

Требует Node.js 14.x или выше, npm для управления пакетами, кошелек с средствами и приватным ключом, а также доступ к блокчейн RPC URL (Infura, Alchemy) для поддерживаемых сетей. Поддерживает типы сделок exactIn и exactOut с настраиваемыми параметрами.