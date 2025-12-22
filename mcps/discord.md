---
title: Discord MCP сервер
description: MCP сервер для интеграции с Discord, который позволяет отправлять сообщения, управлять каналами и взаимодействовать с серверами Discord через API с поддержкой OAuth.
tags:
- Messaging
- API
- Integration
- Cloud
author: Klavis-AI
featured: true
---

MCP сервер для интеграции с Discord, который позволяет отправлять сообщения, управлять каналами и взаимодействовать с серверами Discord через API с поддержкой OAuth.

## Установка

### Klavis Python SDK

```bash
pip install klavis

from klavis import Klavis
klavis = Klavis(api_key="your-free-key")
server = klavis.mcp_server.create_server_instance("DISCORD", "user123")
```

### Klavis NPM SDK

```bash
npm install klavis
```

### Docker

```bash
docker pull ghcr.io/klavis-ai/discord-mcp-server:latest

docker run -p 5000:5000 -e DISCORD_TOKEN=$DISCORD_TOKEN \
  ghcr.io/klavis-ai/discord-mcp-server:latest
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `message_management` | Отправка, редактирование и удаление сообщений |
| `channel_operations` | Управление каналами и правами доступа к каналам |
| `server_management` | Получение информации о сервере и данных участников |
| `user_interactions` | Управление ролями пользователей и правами доступа |
| `bot_operations` | Обработка специфичных для бота функций Discord |

## Возможности

- Управление сообщениями: отправка, редактирование и удаление сообщений
- Операции с каналами: управление каналами и правами доступа к каналам
- Управление сервером: получение информации о сервере и данных участников
- Взаимодействие с пользователями: управление ролями и правами доступа
- Операции бота: обработка специфичных для бота функций Discord
- Поддержка OAuth для интеграции с Discord API

## Переменные окружения

### Обязательные
- `DISCORD_TOKEN` - токен Discord бота для аутентификации в API

## Ресурсы

- [GitHub Repository](https://github.com/Klavis-AI/klavis)

## Примечания

Этот MCP сервер предоставляется Klavis AI с возможностью как хостинга (управляемая инфраструктура с бесплатным API ключом), так и самостоятельного развертывания. Хостинг-сервис рекомендуется для продакшена, поскольку не требует настройки.