---
title: BNBChain MCP сервер
description: Реализация Model Context Protocol, которая обеспечивает бесшовное взаимодействие с BNB Chain и другими EVM-совместимыми сетями через AI-интерфейсы, предоставляя комплексные инструменты для блокчейн-разработки и возможности взаимодействия со смарт-контрактами.
tags:
- Finance
- API
- Integration
- Code
author: bnb-chain
featured: false
---

Реализация Model Context Protocol, которая обеспечивает бесшовное взаимодействие с BNB Chain и другими EVM-совместимыми сетями через AI-интерфейсы, предоставляя комплексные инструменты для блокчейн-разработки и возможности взаимодействия со смарт-контрактами.

## Установка

### NPX

```bash
npx -y @bnb-chain/mcp@latest
```

### Из исходного кода

```bash
git clone https://github.com/bnb-chain/bnbchain-mcp.git
cd bnbchain-mcp
bun install
bun dev:sse
```

## Конфигурация

### Cursor по умолчанию

```json
{
  "mcpServers": {
    "bnbchain-mcp": {
      "command": "npx",
      "args": ["-y", "@bnb-chain/mcp@latest"],
      "env": {
        "PRIVATE_KEY": "your_private_key_here. (optional)"
      }
    }
  }
}
```

### Cursor SSE

```json
{
  "mcpServers": {
    "bnbchain-mcp": {
      "command": "npx",
      "args": ["-y", "@bnb-chain/mcp@latest", "--sse"],
      "env": {
        "PRIVATE_KEY": "your_private_key_here. (optional)"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "bnbchain-mcp": {
      "command": "npx",
      "args": ["-y", "@bnb-chain/mcp@latest"],
      "env": {
        "PRIVATE_KEY": "your_private_key_here"
      }
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "bnbchain-mcp": {
      "url": "http://localhost:3001/sse",
      "env": {
        "PRIVATE_KEY": "your_private_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_block_by_hash` | Получить блок по хешу |
| `get_block_by_number` | Получить блок по номеру |
| `get_latest_block` | Получить последний блок |
| `get_transaction` | Получить подробную информацию о конкретной транзакции по её хешу |
| `get_transaction_receipt` | Получить квитанцию транзакции по её хешу |
| `estimate_gas` | Оценить стоимость газа для транзакции |
| `transfer_native_token` | Переслать нативные токены (BNB, ETH, MATIC и т.д.) на адрес |
| `approve_token_spending` | Разрешить другому адресу тратить ваши ERC20 токены |
| `transfer_nft` | Переслать NFT (ERC721 токен) с одного адреса на другой |
| `transfer_erc1155` | Переслать ERC1155 токены на другой адрес |
| `transfer_erc20` | Переслать ERC20 токены на адрес |
| `get_address_from_private_key` | Получить EVM адрес, полученный из приватного ключа |
| `get_chain_info` | Получить информацию о сети для конкретной блокчейн-сети |
| `get_supported_networks` | Получить список поддерживаемых сетей |
| `resolve_ens` | Преобразовать ENS имя в EVM адрес |

## Возможности

- Запрос и управление блоками блокчейна
- Взаимодействие со смарт-контрактами (операции чтения/записи)
- Информация о сети и управление EVM-совместимыми сетями
- NFT операции (ERC721/ERC1155) включая переводы и метаданные
- Токен операции (ERC20) включая переводы и проверку балансов
- Управление и анализ транзакций
- Операции и управление кошельком
- Управление файлами Greenfield (загрузка, скачивание, операции с корзинами)
- Поддержка BSC, opBNB, Greenfield, Ethereum и других EVM сетей
- Разрешение ENS имён

## Переменные окружения

### Опциональные
- `PRIVATE_KEY` - Приватный ключ вашего кошелька (необходим для операций с транзакциями)
- `LOG_LEVEL` - Установить уровень логирования (DEBUG, INFO, WARN, ERROR)
- `PORT` - Номер порта сервера (по умолчанию: 3001)

## Примеры использования

```
Analyze this address: 0x123...
```

```
Explain the EVM concept of gas
```

```
Check the latest block on BSC
```

## Ресурсы

- [GitHub Repository](https://github.com/bnb-chain/bnbchain-mcp)

## Примечания

Поддерживает как режим по умолчанию, так и SSE режим. Включает комплексную поддержку блокчейна Greenfield для управления файлами и корзинами. Создан с сервером разработки с горячей перезагрузкой, использующим bun. Включает тестовый UI с @modelcontextprotocol/inspector. Основан на open-source проектах от TermiX-official/bsc-mcp и mcpdotdirect/evm-mcp-server.