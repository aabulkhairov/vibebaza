---
title: Xero-mcp-server MCP сервер
description: MCP сервер, который обеспечивает мост между протоколом MCP
  и API Xero, предоставляя стандартизированный доступ к учетным и бизнес-функциям Xero,
  включая управление контактами, выставление счетов и финансовую отчетность.
tags:
- Finance
- API
- Productivity
- Integration
- CRM
author: XeroAPI
featured: true
---

MCP сервер, который обеспечивает мост между протоколом MCP и API Xero, предоставляя стандартизированный доступ к учетным и бизнес-функциям Xero, включая управление контактами, выставление счетов и финансовую отчетность.

## Установка

### NPX

```bash
npx -y @xeroapi/xero-mcp-server@latest
```

### Из исходного кода

```bash
# Используя npm
npm install
npm run build

# Используя pnpm
pnpm install
pnpm build
```

## Конфигурация

### Claude Desktop - Пользовательские подключения

```json
{
  "mcpServers": {
    "xero": {
      "command": "npx",
      "args": ["-y", "@xeroapi/xero-mcp-server@latest"],
      "env": {
        "XERO_CLIENT_ID": "your_client_id_here",
        "XERO_CLIENT_SECRET": "your_client_secret_here"
      }
    }
  }
}
```

### Claude Desktop - Bearer Token

```json
{
  "mcpServers": {
    "xero": {
      "command": "npx",
      "args": ["-y", "@xeroapi/xero-mcp-server@latest"],
      "env": {
        "XERO_CLIENT_BEARER_TOKEN": "your_bearer_token"
      }
    }
  }
}
```

### Claude Desktop - Разработка

```json
{
  "mcpServers": {
    "xero": {
      "command": "node",
      "args": ["insert-your-file-path-here/xero-mcp-server/dist/index.js"],
      "env": {
        "XERO_CLIENT_ID": "your_client_id_here",
        "XERO_CLIENT_SECRET": "your_client_secret_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list-accounts` | Получить список счетов |
| `list-contacts` | Получить список контактов из Xero |
| `list-credit-notes` | Получить список кредитных нот |
| `list-invoices` | Получить список счетов-фактур |
| `list-items` | Получить список товаров |
| `list-organisation-details` | Получить детали об организации |
| `list-profit-and-loss` | Получить отчет о прибылях и убытках |
| `list-quotes` | Получить список котировок |
| `list-tax-rates` | Получить список налоговых ставок |
| `list-payments` | Получить список платежей |
| `list-trial-balance` | Получить оборотно-сальдовый баланс |
| `list-bank-transactions` | Получить список банковских транзакций |
| `list-payroll-employees` | Получить список сотрудников расчета зарплаты |
| `list-report-balance-sheet` | Получить отчет балансового листа |
| `list-payroll-employee-leave` | Получить записи об отпусках сотрудника |

## Возможности

- Аутентификация Xero OAuth2 с пользовательскими подключениями
- Управление контактами
- Управление планом счетов
- Создание и управление счетами-фактурами
- Соответствие протоколу MCP

## Переменные окружения

### Опциональные
- `XERO_CLIENT_ID` - ID клиента приложения Xero для пользовательских подключений
- `XERO_CLIENT_SECRET` - Секрет клиента приложения Xero для пользовательских подключений
- `XERO_CLIENT_BEARER_TOKEN` - Bearer токен для аутентификации (имеет приоритет над client ID/secret)

## Ресурсы

- [GitHub Repository](https://github.com/XeroAPI/xero-mcp-server)

## Примечания

Требует аккаунт разработчика Xero с учетными данными API. Демо-компания рекомендуется для тестирования с предзагруженными образцами данных. Для запросов, связанных с расчетом зарплаты, регион должен быть NZ или UK. XERO_CLIENT_BEARER_TOKEN имеет приоритет над XERO_CLIENT_ID, если оба определены.