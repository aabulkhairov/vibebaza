---
title: jupiter-mcp сервер
description: MCP сервер для выполнения обмена токенов в блокчейне Solana с использованием Jupiter Ultra API, объединяющий DEX роутинг и RFQ для оптимального ценообразования.
tags:
- Finance
- API
- Integration
author: kukapay
featured: false
---

MCP сервер для выполнения обмена токенов в блокчейне Solana с использованием Jupiter Ultra API, объединяющий DEX роутинг и RFQ для оптимального ценообразования.

## Установка

### Из исходного кода

```bash
git clone https://github.com/kukapay/jupiter-mcp.git
cd jupiter-mcp
npm install
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "Jupiter-MCP": {
      "command": "node",
      "args": ["path/to/jupiter-mcp/server/index.js"],
      "env": {
        "SOLANA_RPC_URL": "solana rpc url you can access",
        "PRIVATE_KEY": "your private key"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-ultra-order` | Получает ордер на обмен из Jupiter Ultra API, используя как DEX роутинг, так и RFQ для оптимального це... |
| `execute-ultra-order` | Просит Jupiter выполнить транзакцию обмена от имени владельца кошелька, обрабатывая проскальзывание... |

## Возможности

- Получение ордеров на обмен из Jupiter Ultra API, объединяющего DEX роутинг и RFQ (Request for Quote) для оптимального ценообразования
- Выполнение обменов через Jupiter Ultra API с обработкой проскальзывания, приоритетных комиссий и посадки транзакций

## Переменные окружения

### Обязательные
- `SOLANA_RPC_URL` - Доступ к ноде Solana RPC (например, https://api.mainnet-beta.solana.com)
- `PRIVATE_KEY` - Приватный ключ (в кодировке base58) для подписи транзакций

## Примеры использования

```
Get a swap order to trade 1.23 SOL for USDC
```

```
Execute the swap order with request ID 'a770110b-82c9-46c8-ba61-09d955b27503' using the transaction provided
```

## Ресурсы

- [GitHub Repository](https://github.com/kukapay/jupiter-mcp)

## Примечания

Требует Node.js версии 18 или выше для нативной поддержки fetch. Необходим кошелек Solana с приватным ключом и доступ к эндпойнту Solana RPC.