---
title: Edwin MCP сервер
description: MCP сервер для Edwin SDK, который позволяет AI агентам взаимодействовать с DeFi протоколами и выполнять операции с кошельками в блокчейнах EVM и Solana через стандартизированный протокол.
tags:
- Finance
- API
- Integration
- Security
author: Community
featured: false
---

MCP сервер для Edwin SDK, который позволяет AI агентам взаимодействовать с DeFi протоколами и выполнять операции с кошельками в блокчейнах EVM и Solana через стандартизированный протокол.

## Установка

### Из исходного кода

```bash
cd examples/mcp-server
pnpm install
pnpm build
```

## Конфигурация

### Claude Desktop

```json
Use the provided claude_desktop_config.json file - Open Claude Desktop, go to Settings, and import the configuration from claude_desktop_config.json
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `wallet_operations` | Выполнение операций с кошельком |
| `balance_checking` | Проверка балансов кошелька |
| `transaction_signing` | Подписание транзакций |
| `token_transfers` | Переводы токенов |
| `contract_interactions` | Взаимодействие со смарт-контрактами |

## Возможности

- Интеграция с инструментами Edwin SDK
- Поддержка блокчейнов EVM и Solana
- Операции с кошельками и проверка балансов
- Подписание транзакций и переводы токенов
- Взаимодействие со смарт-контрактами
- Горячая перезагрузка для разработки

## Переменные окружения

### Обязательные
- `SOLANA_RPC_URL` - Ваш RPC эндпоинт для Solana
- `EVM_PRIVATE_KEY` - Приватный ключ вашего EVM кошелька
- `SOLANA_PRIVATE_KEY` - Приватный ключ вашего Solana кошелька
- `EDWIN_MCP_MODE` - Включить режим MCP (установить в true)

## Ресурсы

- [GitHub Repository](https://github.com/edwin-finance/edwin)

## Примечания

Требуется Node.js >= 18.0.0 и pnpm. Никогда не коммитьте приватные ключи и держите их в безопасности. Сервер предоставляет доступ ко всем инструментам, настроенным в вашем экземпляре Edwin. Может запускаться в продакшн режиме с 'pnpm start' или в режиме разработки с 'pnpm dev'.