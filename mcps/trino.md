---
title: Trino MCP сервер
description: Высокопроизводительный Model Context Protocol (MCP) сервер для Trino, реализованный на Go, который позволяет AI-ассистентам легко взаимодействовать с распределенным SQL движком Trino через стандартизированные MCP инструменты.
tags:
- Database
- Analytics
- API
- Integration
- Cloud
author: tuannvm
featured: false
---

Высокопроизводительный Model Context Protocol (MCP) сервер для Trino, реализованный на Go, который позволяет AI-ассистентам легко взаимодействовать с распределенным SQL движком Trino через стандартизированные MCP инструменты.

## Установка

### Homebrew

```bash
brew install tuannvm/mcp/mcp-trino
```

### Установка одной командой

```bash
curl -fsSL https://raw.githubusercontent.com/tuannvm/mcp-trino/main/install.sh | bash
```

### Локальная разработка

```bash
export TRINO_HOST=localhost TRINO_USER=trino
mcp-trino
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `execute_query` | Выполнение SQL запросов в Trino |
| `list_catalogs` | Список доступных каталогов в Trino |
| `list_schemas` | Список схем в каталогах |
| `list_tables` | Список таблиц в схемах |
| `get_table_schema` | Получение определения схемы таблицы |
| `explain_query` | Получение плана выполнения запроса |

## Возможности

- Реализация MCP сервера на Go
- Выполнение SQL запросов Trino через MCP инструменты
- Обнаружение каталогов, схем и таблиц
- Поддержка Docker контейнеров
- Поддержка STDIO и HTTP транспортов
- OAuth 2.1 аутентификация с 4 провайдерами (HMAC, Okta, Google, Azure AD)
- Нативный и прокси режимы OAuth
- Поддержка StreamableHTTP с JWT аутентификацией
- Обратная совместимость с SSE эндпоинтами
- Совместимость с Cursor, Claude Desktop, Windsurf, ChatWise

## Переменные окружения

### Обязательные
- `TRINO_HOST` - Хост Trino сервера
- `TRINO_USER` - Имя пользователя Trino

### Опциональные
- `TRINO_SCHEME` - Схема подключения для Trino
- `MCP_TRANSPORT` - Режим транспорта (STDIO или HTTP)
- `OAUTH_PROVIDER` - OAuth провайдер (okta, google, azure)
- `OAUTH_ENABLED` - Включить OAuth аутентификацию
- `OAUTH_MODE` - Режим OAuth (native или proxy)
- `OIDC_ISSUER` - URL OIDC эмитента
- `OIDC_AUDIENCE` - OIDC аудитория
- `OIDC_CLIENT_ID` - OAuth client ID

## Ресурсы

- [GitHub Repository](https://github.com/tuannvm/mcp-trino)

## Примечания

Этот проект использует oauth-mcp-proxy - самостоятельную OAuth 2.1 библиотеку для Go MCP серверов. Для продакшн деплоя смотрите Руководство по развертыванию и документацию по архитектуре OAuth. Сервер поддерживает множество источников данных через Trino, включая PostgreSQL, MySQL, S3/Hive, BigQuery и MongoDB.