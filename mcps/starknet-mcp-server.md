---
title: Starknet MCP сервер
description: Комплексный MCP сервер для блокчейна Starknet, который предоставляет
  AI агентам возможность взаимодействовать с сетями Starknet, запрашивать данные
  блокчейна, управлять кошельками и взаимодействовать со смарт-контрактами.
tags:
- Finance
- API
- Integration
- Analytics
- Code
author: Community
featured: false
install_command: claude mcp add starknet-mcp-server npx @mcpdotdirect/starknet-mcp-server
---

Комплексный MCP сервер для блокчейна Starknet, который предоставляет AI агентам возможность взаимодействовать с сетями Starknet, запрашивать данные блокчейна, управлять кошельками и взаимодействовать со смарт-контрактами.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @mcpdotdirect/starknet-mcp-server --client claude
```

### NPX (Direct)

```bash
npx @mcpdotdirect/starknet-mcp-server
```

### Global NPM

```bash
npm install -g @mcpdotdirect/starknet-mcp-server
```

### Local Project

```bash
npm install @mcpdotdirect/starknet-mcp-server
```

### From Source

```bash
git clone https://github.com/mcpdotdirect/starknet-mcp-server.git
cd starknet-mcp-server
npm install
npm start
```

## Конфигурация

### Cursor MCP.json

```json
{
  "mcpServers": {
    "starknet-mcp-server": {
      "command": "npx",
      "args": [
        "@mcpdotdirect/starknet-mcp-server"
      ]
    },
    "starknet-mcp-http": {
      "command": "npx",
      "args": [
        "@mcpdotdirect/starknet-mcp-server",
        "http"
      ]
    }
  }
}
```

### HTTP режим с SSE

```json
{
  "mcpServers": {
    "starknet-mcp-sse": {
      "url": "http://localhost:3000/sse"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_starknet_chain_info` | Получить информацию о сети Starknet |
| `get_supported_starknet_networks` | Получить список поддерживаемых сетей Starknet |
| `get_starknet_eth_balance` | Получить баланс ETH для адреса Starknet или Starknet ID |
| `get_starknet_token_balance` | Получить баланс любого токена для адреса |
| `get_starknet_strk_balance` | Получить баланс токена STRK для адреса |
| `get_starknet_native_balances` | Получить все балансы нативных токенов (ETH и STRK) для адреса |
| `resolve_starknet_name` | Получить Starknet ID для адреса |
| `resolve_starknet_address` | Получить адрес для Starknet ID |
| `get_starknet_profile` | Получить полный профиль Starknet ID для адреса |
| `validate_starknet_domain` | Проверить, является ли строка валидным Starknet ID |
| `get_starknet_block` | Получить информацию о конкретном блоке |
| `get_starknet_block_transactions` | Получить транзакции в конкретном блоке |
| `get_starknet_transaction` | Получить детали о транзакции |
| `get_starknet_transaction_receipt` | Получить квитанцию транзакции |
| `check_starknet_transaction_status` | Проверить, подтверждена ли транзакция |

## Возможности

- Полная интеграция с блокчейном Starknet, используя Starknet.js
- Поддержка Mainnet и тестовой сети Sepolia
- Интеграция StarknetID для разрешения удобочитаемых идентификаторов
- Поддержка нативных токенов ETH и STRK
- Взаимодействие со смарт-контрактами (операции чтения и записи)
- Два режима транспорта (stdio сервер и HTTP сервер)
- Дизайн, готовый для AI, подходящий для Claude, GPT и других ассистентов
- Операции с NFT и просмотр метаданных
- Возможности перевода токенов с удобочитаемыми суммами
- Мониторинг транзакций и проверка статуса

## Примеры использования

```
Проверить баланс ETH для vitalik.stark
```

```
Получить информацию о последнем блоке в Starknet
```

```
Найти владельца NFT #123 в коллекции 0x...
```

```
Перевести 1 ETH с моего аккаунта на другой адрес
```

```
Разрешить адрес для Starknet ID
```

## Ресурсы

- [GitHub Repository](https://github.com/mcpdotdirect/starknet-mcp-server)

## Примечания

Каждый инструмент, который принимает адреса Starknet, также поддерживает StarknetID, автоматически разрешая удобочитаемые идентификаторы в адреса. Сервер по умолчанию работает на порту 3000 в HTTP режиме и поддерживает как stdio, так и HTTP режимы транспорта для различных потребностей интеграции.