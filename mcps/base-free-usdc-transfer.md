---
title: Base Free USDC Transfer MCP сервер
description: MCP сервер для бесплатных переводов USDC в блокчейне Base с использованием интеграции Coinbase CDP MPC Wallet и поддержкой резолюции доменов ENS и BaseName.
tags:
- Finance
- API
- Integration
- Security
author: magnetai
featured: false
---

MCP сервер для бесплатных переводов USDC в блокчейне Base с использованием интеграции Coinbase CDP MPC Wallet и поддержкой резолюции доменов ENS и BaseName.

## Установка

### NPX

```bash
npx -y @magnetai/free-usdc-transfer
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "free-usdc-transfer": {
      "command": "npx",
      "args": [
        "-y",
        "@magnetai/free-usdc-transfer"
      ],
      "env": {
        "COINBASE_CDP_API_KEY_NAME": "YOUR_COINBASE_CDP_API_KEY_NAME",
        "COINBASE_CDP_PRIVATE_KEY": "YOUR_COINBASE_CDP_PRIVATE_KEY"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `tranfer-usdc` | Анализирует стоимость купленных товаров и переводит USDC получателю через сеть Base с автомати... |
| `create_coinbase_mpc_wallet` | Создает адрес Coinbase MPC кошелька и сохраняет seed в защищенный файл |

## Возможности

- Бесплатные переводы USDC в блокчейне Base без комиссий
- Создание и управление Coinbase MPC Wallet для безопасных транзакций
- Автоматическая резолюция доменов ENS и BaseName
- Планирование транзакций без ожидания завершения
- Интеграция с BaseScan для отслеживания транзакций

## Переменные окружения

### Обязательные
- `COINBASE_CDP_API_KEY_NAME` - Имя API ключа Coinbase CDP из панели разработчика
- `COINBASE_CDP_PRIVATE_KEY` - Приватный ключ Coinbase CDP из панели разработчика

## Ресурсы

- [GitHub Repository](https://github.com/magnetai/mcp-free-usdc-transfer)

## Примечания

Требуется аккаунт Coinbase CDP и API ключ. Seed MPC кошелька сохраняется в директории Documents как mcp_info.json. Также может быть установлен с magnet-desktop. Лицензия MIT License.