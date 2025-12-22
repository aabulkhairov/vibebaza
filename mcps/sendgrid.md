---
title: SendGrid MCP сервер
description: MCP сервер, который интегрируется с SendGrid API v3, позволяя AI-ассистентам отправлять письма, управлять шаблонами и отслеживать статистику электронной почты.
tags:
- Messaging
- API
- Analytics
- Integration
- Productivity
author: recepyavuz0
featured: false
---

MCP сервер, который интегрируется с SendGrid API v3, позволяя AI-ассистентам отправлять письма, управлять шаблонами и отслеживать статистику электронной почты.

## Установка

### Из исходного кода

```bash
git clone https://github.com/recepyavuz0/sendgrid-mcp-server.git
cd sendgrid-mcp-server
npm install
npm run build
```

### NPX

```bash
npx -y sendgrid-api-mcp-server
```

### Автономный запуск

```bash
npm start
```

## Конфигурация

### Cursor IDE

```json
{
  "mcpServers": {
    "sendgrid-api-mcp-server": {
      "command": "npx",
      "args": ["-y", "sendgrid-api-mcp-server"],
      "env": {
        "SENDGRID_API_KEY": "your_api_key",
        "FROM_EMAIL": "your_email@domain.com"
      }
    }
  }
}
```

### Claude Desktop

```json
{
  "mcpServers": {
    "sendgrid-api-mcp-server": {
      "command": "npx",
      "args": ["-y", "sendgrid-api-mcp-server"],
      "env": {
        "SENDGRID_API_KEY": "your_api_key",
        "FROM_EMAIL": "your_email@domain.com"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `sendEmail` | Отправка обычных писем в текстовом или HTML формате |
| `sendEmailWithTemplate` | Отправка динамических писем с использованием готовых шаблонов |
| `sendBatchEmails` | Отправка писем нескольким получателям одновременно |
| `listTemplates` | Просмотр существующих шаблонов писем |
| `getStats` | Получение статистики писем за определенный период |
| `scheduleEmail` | Планирование отправки письма на будущую дату |
| `createTemplate` | Создание нового динамического шаблона письма |

## Возможности

- Отправка отдельных писем в текстовом или HTML формате
- Массовая отправка писем нескольким получателям
- Письма на основе шаблонов с динамическим контентом
- Запланированные письма для отправки в будущем
- Просмотр и создание шаблонов
- Статистика и отчеты по электронной почте с указанием периодов
- Ежедневные, еженедельные или ежемесячные отчеты

## Переменные окружения

### Обязательные
- `SENDGRID_API_KEY` - API ключ, полученный из вашего аккаунта SendGrid
- `FROM_EMAIL` - Подтвержденный email адрес отправителя в SendGrid

## Примеры использования

```
Send a project meeting reminder to john@example.com
```

```
Send an HTML welcome message to user@test.com
```

```
Send a meeting reminder to ali@example.com: 'We'll meet tomorrow at 2:00 PM.'
```

```
Send email to user@test.com using template d-123456789 with data: {name: 'John', company: 'ABC Corp'}
```

```
Send new feature announcement to john@test.com, jane@test.com, bob@test.com
```

## Ресурсы

- [GitHub Repository](https://github.com/recepyavuz0/sendgrid-mcp-server)

## Примечания

Совместим с Zed Editor, VS Code MCP Extension, Continue.dev и другими MCP клиентами. Требует аккаунт SendGrid и подтвержденный email адрес отправителя. Работает через stdin/stdout с использованием стандартного MCP протокола.