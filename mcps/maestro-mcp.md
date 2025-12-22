---
title: Maestro MCP сервер
description: Model Context Protocol (MCP) сервер для взаимодействия с Bitcoin через платформу Maestro API. Предоставляет инструменты для исследования блоков, транзакций, адресов и многого другого в блокчейне Bitcoin.
tags:
- Finance
- API
- Analytics
- Monitoring
author: Community
featured: false
---

Model Context Protocol (MCP) сервер для взаимодействия с Bitcoin через платформу Maestro API. Предоставляет инструменты для исследования блоков, транзакций, адресов и многого другого в блокчейне Bitcoin.

## Установка

### Из исходников

```bash
# Install dependencies
npm install

# Build the project
npm run build

# Copy and edit environment variables
cp .env.example .env
# Edit .env to add your Maestro API key and any other config
```

### Запуск сервера

```bash
npm run start:http
```

## Возможности

- Потоковый HTTP MCP сервер
- Аутентификация через API ключ
- Blockchain Indexer API
- Mempool Monitoring API
- Market Price API
- Wallet API
- Node RPC API
- Поддержка сетей Bitcoin Mainnet и Testnet4

## Переменные окружения

### Обязательные
- `MAESTRO_API_KEY` - API ключ для аутентификации на платформе Maestro

### Опциональные
- `API_BASE_URL` - Базовый URL для Maestro API (Mainnet: https://xbt-mainnet.gomaestro-api.org/v0, Testnet4: https://xbt-testnet.gomaestro-api.org/v0)
- `PORT` - Порт для HTTP сервера (по умолчанию: 3000)

## Ресурсы

- [GitHub Repository](https://github.com/maestro-org/maestro-mcp)

## Примечания

Хостинговые версии доступны по адресам https://xbt-mainnet.gomaestro-api.org/v0/mcp (Mainnet) и https://xbt-testnet.gomaestro-api.org/v0/mcp (Testnet4). Требуется Node.js версии 20 или выше. Сервер сгенерирован с помощью openapi-mcp-generator. Примеры клиентов доступны по адресу https://github.com/maestro-org/maestro-mcp-client-examples.