---
title: Holaspirit MCP сервер
description: Model Context Protocol сервер, который предоставляет доступ к API Holaspirit, позволяя AI-ассистентам взаимодействовать с организационными данными вроде задач, метрик, кругов, ролей, встреч и многого другого через стандартизированный интерфейс.
tags:
- API
- Productivity
- Integration
- Analytics
- CRM
author: Community
featured: false
install_command: npx -y @smithery/cli install holaspirit-mcp-server --client claude
---

Model Context Protocol сервер, который предоставляет доступ к API Holaspirit, позволяя AI-ассистентам взаимодействовать с организационными данными вроде задач, метрик, кругов, ролей, встреч и многого другого через стандартизированный интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install holaspirit-mcp-server --client claude
```

### NPM

```bash
npm install holaspirit-mcp-server
```

## Конфигурация

### Claude Desktop (Stdio)

```json
{
  "holaspirit": {
    "command": "npx",
    "args": [
      "-y",
      "holaspirit-mcp-server"
    ],
    "env": {
      "HOLASPIRIT_API_TOKEN": "<your token>",
      "HOLASPIRIT_ORGANIZATION_ID": "<your org id>"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `holaspirit_list_tasks` | Показать все задачи в организации |
| `holaspirit_list_metrics` | Показать все метрики в организации |
| `holaspirit_list_circles` | Показать все круги в организации |
| `holaspirit_get_circle` | Получить детали конкретного круга |
| `holaspirit_list_roles` | Показать все роли в организации |
| `holaspirit_get_role` | Получить детали конкретной роли |
| `holaspirit_list_domains` | Показать все домены в организации |
| `holaspirit_list_policies` | Показать все политики в организации |
| `holaspirit_list_meetings` | Показать все встречи в организации |
| `holaspirit_get_meeting` | Получить детали конкретной встречи |
| `holaspirit_get_member_feed` | Получить ленту участника |
| `holaspirit_get_tensions` | Получить напряжения для встречи или встреч |
| `holaspirit_search_member` | Найти участника по email |

## Возможности

- Доступ к API Holaspirit через стандартизированный интерфейс MCP
- Поддержка режимов транспорта stdio и HTTP
- Полный доступ к организационным данным включая задачи, метрики, круги, роли, домены, политики, встречи и информацию об участниках
- Отслеживание напряжений во встречах и возможности поиска участников

## Переменные окружения

### Обязательные
- `HOLASPIRIT_API_TOKEN` - Ваш токен API Holaspirit
- `HOLASPIRIT_ORGANIZATION_ID` - ID вашей организации в Holaspirit

## Ресурсы

- [GitHub Repository](https://github.com/syucream/holaspirit-mcp-server)

## Примечания

Поддерживает как stdio транспорт (по умолчанию), так и режим HTTP транспорта. Для HTTP транспорта запускается с флагом --port и принимает POST запросы на любой путь используя протокол Streamable HTTP. Переменные окружения можно задать через .env файл или напрямую в конфигурации.