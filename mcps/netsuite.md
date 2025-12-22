---
title: NetSuite MCP сервер
description: MCP сервер, который предоставляет безопасный доступ к данным ERP системы NetSuite через OAuth 2.0 с PKCE аутентификацией, позволяя делать запросы на естественном языке для получения бизнес-данных, отчетов и операций.
tags:
- CRM
- API
- Integration
- Analytics
- Finance
author: dsvantien
featured: false
---

MCP сервер, который предоставляет безопасный доступ к данным ERP системы NetSuite через OAuth 2.0 с PKCE аутентификацией, позволяя делать запросы на естественном языке для получения бизнес-данных, отчетов и операций.

## Установка

### NPX (Рекомендуется)

```bash
npx @suiteinsider/netsuite-mcp@latest
```

### Из исходного кода

```bash
git clone https://github.com/dsvantien/netsuite-mcp-server.git
cd netsuite-mcp-server
npm install
npm link
```

## Конфигурация

### Claude Desktop (с npx)

```json
{
  "mcpServers": {
    "netsuite": {
      "command": "npx",
      "args": ["@suiteinsider/netsuite-mcp@latest"],
      "env": {
        "NETSUITE_ACCOUNT_ID": "your-account-id",
        "NETSUITE_CLIENT_ID": "your-client-id",
        "OAUTH_CALLBACK_PORT": "8080"
      }
    }
  }
}
```

### Локальная разработка

```json
{
  "mcpServers": {
    "netsuite": {
      "command": "node",
      "args": ["/absolute/path/to/netsuite-mcp-server/src/index.js"],
      "env": {
        "NETSUITE_ACCOUNT_ID": "your-account-id",
        "NETSUITE_CLIENT_ID": "your-client-id",
        "OAUTH_CALLBACK_PORT": "8080"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `ns_runCustomSuiteQL` | Выполнение SuiteQL запросов |
| `ns_listAllReports` | Список доступных финансовых отчетов |
| `ns_runReport` | Выполнение конкретного отчета |
| `ns_listSavedSearches` | Список сохраненных поисков |
| `ns_runSavedSearch` | Выполнение сохраненного поиска |
| `ns_getRecord` | Получение конкретной записи |
| `ns_createRecord` | Создание новой записи |
| `ns_updateRecord` | Обновление существующей записи |
| `netsuite_authenticate` | Аутентификация с NetSuite через OAuth 2.0 |
| `netsuite_logout` | Очистка сессии NetSuite и выход |

## Возможности

- OAuth 2.0 с PKCE - Безопасная аутентификация без клиентских секретов
- Автоматическое обновление токенов - Токены обновляются автоматически до истечения срока
- Поддержка переменных окружения - Настройка учетных данных один раз в конфигурации MCP
- Сохранение сессий - Аутентификация сохраняется при перезапуске сервера
- Универсальная интеграция с MCP - Работает с Claude Code, Cursor IDE, Gemini CLI и другими MCP клиентами
- Инструменты NetSuite MCP - Доступ ко всем возможностям NetSuite MCP (SuiteQL, отчеты, сохраненные поиски и др.)
- Модульная архитектура - Чистая, поддерживаемая кодовая база, следующая принципу единственной ответственности

## Переменные окружения

### Обязательные
- `NETSUITE_ACCOUNT_ID` - ID вашего аккаунта NetSuite
- `NETSUITE_CLIENT_ID` - ID вашего OAuth клиента

### Опциональные
- `OAUTH_CALLBACK_PORT` - Порт для OAuth callback (по умолчанию: 8080)

## Примеры использования

```
Authenticate with NetSuite
```

```
Show me all customers
```

```
List available saved searches
```

```
Run a SuiteQL query to get sales orders from last month
```

```
Execute the "Monthly Revenue" report
```

## Ресурсы

- [GitHub Repository](https://github.com/dsvantien/netsuite-mcp-server)

## Примечания

Требует установки и настройки NetSuite AI Connector SuiteApp (Bundle ID: 522506). Вы должны создать запись интеграции OAuth в NetSuite с включенными Public Client и Authorization Code Grant. После аутентификации перезапустите чат или переподключите MCP сервер, чтобы увидеть инструменты NetSuite.