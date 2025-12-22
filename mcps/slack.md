---
title: Slack MCP сервер
description: Model Context Protocol (MCP) сервер для взаимодействия с рабочими пространствами Slack,
  предоставляющий инструменты для получения списка каналов, отправки сообщений,
  ответов в тредах, добавления реакций, получения истории каналов и управления пользователями.
tags:
- Messaging
- Integration
- API
- Productivity
author: zencoderai
featured: false
---

Model Context Protocol (MCP) сервер для взаимодействия с рабочими пространствами Slack, предоставляющий инструменты для получения списка каналов, отправки сообщений, ответов в тредах, добавления реакций, получения истории каналов и управления пользователями.

## Установка

### NPM Global

```bash
npm install -g @zencoderai/slack-mcp-server
```

### Из исходников

```bash
npm install
npm run build
```

### Docker

```bash
docker build -t slack-mcp-server .
# Или скачать с Docker Hub
docker pull zencoderai/slack-mcp:latest
# Или скачать конкретную версию
docker pull zencoderai/slack-mcp:1.0.0
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `slack_list_channels` | Получить список публичных или предопределённых каналов в рабочем пространстве |
| `slack_post_message` | Отправить новое сообщение в Slack канал |
| `slack_reply_to_thread` | Ответить в конкретном треде сообщения |
| `slack_add_reaction` | Добавить эмодзи реакцию к сообщению |
| `slack_get_channel_history` | Получить недавние сообщения из канала |
| `slack_get_thread_replies` | Получить все ответы в треде сообщения |
| `slack_get_users` | Получить список пользователей рабочего пространства с базовой информацией профиля |
| `slack_get_user_profile` | Получить детальную информацию профиля для конкретного пользователя |

## Возможности

- Поддержка нескольких транспортов (stdio и Streamable HTTP)
- Современный MCP SDK (v1.13.2) с современными API
- Комплексная интеграция со Slack
- Bearer токен аутентификация для HTTP транспорта
- Управление сессиями для HTTP транспорта
- Поддержка предопределённых каналов
- Поддержка пагинации для каналов и пользователей

## Переменные окружения

### Обязательные
- `SLACK_BOT_TOKEN` - Bot User OAuth токен, который начинается с 'xoxb-'
- `SLACK_TEAM_ID` - Ваш team ID, который начинается с 'T'

### Опциональные
- `SLACK_CHANNEL_IDS` - Список предопределённых каналов через запятую
- `AUTH_TOKEN` - Bearer токен для HTTP авторизации (только для Streamable HTTP транспорта)

## Ресурсы

- [GitHub Repository](https://github.com/zencoderai/slack-mcp-server)

## Примечания

Требует создания Slack приложения с определёнными OAuth скоупами: channels:history, channels:read, chat:write, reactions:write, users:read, users.profile:read. Поддерживает как stdio, так и Streamable HTTP транспорты. Расширенная версия оригинальной реализации Anthropic с существенными модификациями от For Good AI Inc.