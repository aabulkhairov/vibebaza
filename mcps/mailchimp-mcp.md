---
title: Mailchimp MCP сервер
description: MCP сервер, который предоставляет доступ только для чтения к Mailchimp Marketing API для комплексного получения данных email-маркетинга.
tags:
- CRM
- Analytics
- API
- Integration
- Messaging
author: Community
featured: false
---

MCP сервер, который предоставляет доступ только для чтения к Mailchimp Marketing API для комплексного получения данных email-маркетинга.

## Установка

### NPX

```bash
npx @agentx-ai/mailchimp-mcp-server
```

### Из исходного кода

```bash
git clone repository
npm install
npm run build
```

## Конфигурация

### MCP клиент

```json
{
  "mcpServers": {
    "mailchimp": {
      "command": "npx",
      "args": ["@agentx-ai/mailchimp-mcp-server"],
      "env": {
        "MAILCHIMP_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_automations` | Выводит список всех автоматизаций в вашем аккаунте Mailchimp |
| `get_automation` | Получает детали конкретной автоматизации по ID рабочего процесса |
| `list_automation_emails` | Выводит список всех писем в автоматизации |
| `get_automation_email` | Получает детали конкретного письма в автоматизации |
| `list_automation_subscribers` | Выводит список подписчиков в очереди email автоматизации |
| `get_automation_queue` | Получает очередь email автоматизации |
| `list_lists` | Выводит список всех списков в вашем аккаунте Mailchimp |
| `get_list` | Получает детали конкретного списка |
| `list_campaigns` | Выводит список всех кампаний в вашем аккаунте Mailchimp |
| `get_campaign` | Получает детали конкретной кампании |
| `list_members` | Выводит список всех участников в конкретном списке |
| `get_member` | Получает детали конкретного участника |
| `list_segments` | Выводит список всех сегментов в конкретном списке |
| `get_segment` | Получает детали конкретного сегмента |
| `list_templates` | Выводит список всех шаблонов в вашем аккаунте Mailchimp |

## Возможности

- Управление автоматизациями (классические автоматизации, не automation flows)
- Управление email автоматизациями и мониторинг очередей
- Управление списками и участниками
- Управление кампаниями и отчетность
- Управление сегментами
- Управление шаблонами
- Отчеты и аналитика для кампаний и автоматизаций
- Получение информации об аккаунте
- Интеграция с менеджером папок и файлов
- Управление лендингами

## Переменные окружения

### Обязательные
- `MAILCHIMP_API_KEY` - Ваш API ключ Mailchimp (должен включать суффикс дата-центра, например, xxxxxxxxxxxxxxxx-us1)

## Ресурсы

- [GitHub Repository](https://github.com/AgentX-ai/mailchimp-mcp)

## Примечания

Этот сервер предоставляет доступ только для чтения к Mailchimp Marketing API v3. Endpoints автоматизаций работают только с классическими автоматизациями, не с automation flows (пока недоступны в API). API ключ должен включать суффикс дата-центра.