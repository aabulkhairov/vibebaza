---
title: Microsoft Teams MCP сервер
description: MCP сервер для интеграции с Microsoft Teams, который позволяет AI ассистентам читать сообщения, создавать треды, отвечать на сообщения, упоминать пользователей и управлять командными коммуникациями.
tags:
- Messaging
- Integration
- Productivity
- API
author: Community
featured: false
---

MCP сервер для интеграции с Microsoft Teams, который позволяет AI ассистентам читать сообщения, создавать треды, отвечать на сообщения, упоминать пользователей и управлять командными коммуникациями.

## Установка

### Из исходного кода

```bash
git clone [repository-url]
cd mcp-teams-server
uv venv
uv sync --frozen --all-extras --dev
```

### Docker сборка

```bash
docker build . -t inditextech/mcp-teams-server
```

### Docker загрузка

```bash
docker pull ghcr.io/inditextech/mcp-teams-server:latest
```

## Возможности

- Создание тредов в канале с заголовком и содержимым, упоминание пользователей
- Обновление существующих тредов с ответами, упоминание пользователей
- Чтение ответов в тредах
- Список участников команды канала
- Чтение сообщений канала

## Переменные окружения

### Обязательные
- `TEAMS_APP_ID` - UUID для вашего MS Entra ID application ID
- `TEAMS_APP_PASSWORD` - Client secret
- `TEAMS_APP_TYPE` - SingleTenant или MultiTenant
- `TEAM_ID` - MS Teams Group Id или Team Id
- `TEAMS_CHANNEL_ID` - MS Teams Channel ID с экранированными символами URL

### Опциональные
- `TEAMS_APP_TENANT_ID` - UUID тенанта в случае SingleTenant

## Ресурсы

- [GitHub Repository](https://github.com/InditexTech/mcp-teams-server)

## Примечания

Требует аккаунт Microsoft Teams с правильной настройкой Azure. Включает предсобранные Docker образы. Интеграционные тесты требуют дополнительные переменные окружения (TEST_THREAD_ID, TEST_MESSAGE_ID, TEST_USER_NAME). Смотрите MS-Teams-setup.md для подробного руководства по конфигурации.