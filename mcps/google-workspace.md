---
title: Google Workspace MCP сервер
description: Готовый к продакшену MCP сервер, обеспечивающий полный контроль естественным языком над всеми основными сервисами Google Workspace включая Gmail, Drive, Calendar, Docs, Sheets, Slides, Forms, Tasks и Chat с поддержкой OAuth 2.1 для множества пользователей.
tags:
- Productivity
- Cloud
- Integration
- API
- Messaging
author: taylorwilsdon
featured: true
---

Готовый к продакшену MCP сервер, обеспечивающий полный контроль естественным языком над всеми основными сервисами Google Workspace включая Gmail, Drive, Calendar, Docs, Sheets, Slides, Forms, Tasks и Chat с поддержкой OAuth 2.1 для множества пользователей.

## Установка

### Установка в один клик для Claude Desktop (DXT)

```bash
Download google_workspace_mcp.dxt from Releases page and double-click to install
```

### UVX

```bash
uvx workspace-mcp --tool-tier core
```

### UV Run

```bash
uv run main.py --tools gmail drive
```

## Возможности

- Полное управление Gmail с комплексным покрытием функций
- Полноценное управление календарем с продвинутыми возможностями
- Операции с файлами с поддержкой Office форматов
- Создание, редактирование и комментирование документов с точным редактированием
- Создание форм, настройки публикации и управление ответами
- Управление пространствами и возможности обмена сообщениями
- Операции с таблицами с гибким управлением ячейками
- Создание презентаций, обновления и манипулирование контентом
- Продвинутая поддержка OAuth 2.0 и OAuth 2.1 с автоматическим обновлением токенов
- Аутентификация bearer токенов для множества пользователей

## Переменные окружения

### Обязательные
- `GOOGLE_OAUTH_CLIENT_ID` - OAuth client ID из Google Cloud
- `GOOGLE_OAUTH_CLIENT_SECRET` - OAuth client secret из Google Cloud

### Опциональные
- `OAUTHLIB_INSECURE_TRANSPORT` - Установите в 1 для разработки, чтобы разрешить HTTP redirect URI
- `USER_GOOGLE_EMAIL` - Email по умолчанию для аутентификации одного пользователя
- `GOOGLE_PSE_API_KEY` - API ключ для функциональности Custom Search
- `GOOGLE_PSE_ENGINE_ID` - Search Engine ID для Custom Search
- `MCP_ENABLE_OAUTH21` - Установите в true для поддержки OAuth 2.1
- `EXTERNAL_OAUTH21_PROVIDER` - Установите в true для внешнего OAuth потока с bearer токенами
- `WORKSPACE_MCP_STATELESS_MODE` - Установите в true для работы без состояния
- `WORKSPACE_MCP_BASE_URI` - Базовый URI сервера (без порта)

## Ресурсы

- [GitHub Repository](https://github.com/taylorwilsdon/google_workspace_mcp)

## Примечания

Требует Google Cloud Project с OAuth 2.0 учетными данными и включенными API (Calendar, Drive, Gmail, Docs, Sheets, Slides, Forms, Tasks, Chat, Custom Search). Поддерживает аутентификацию как для одного пользователя, так и для множества пользователей. Использует Google Desktop OAuth клиенты, исключающие необходимость настройки redirect URI. Включает инновационную CORS прокси архитектуру и Desktop Extensions (DXT) для установки в один клик.