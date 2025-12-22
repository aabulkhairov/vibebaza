---
title: Descope MCP сервер
description: MCP сервер, который предоставляет интерфейс для взаимодействия с Management API Descope, позволяя искать и получать информацию, связанную с проектом, включая логи аудита и управление пользователями.
tags:
- Security
- API
- Integration
- Productivity
author: descope-sample-apps
featured: false
---

MCP сервер, который предоставляет интерфейс для взаимодействия с Management API Descope, позволяя искать и получать информацию, связанную с проектом, включая логи аудита и управление пользователями.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @descope-sample-apps/descope-mcp-server --client claude
```

### Из исходного кода

```bash
git clone https://github.com/descope-sample-apps/descope-mcp-server.git
cd descope-mcp-server
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "descope": {
      "command": "node",
      "args": ["/path/to/descope-mcp-server/build/index.js"],
      "env": {
        "DESCOPE_PROJECT_ID": "your-descope-project-id-here",
        "DESCOPE_MANAGEMENT_KEY": "your-descope-management-key-here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `search-audits` | Получает до 10 записей логов аудита из вашего проекта Descope |
| `search-users` | Получает до 10 записей пользователей из вашего проекта Descope |
| `create-user` | Создает нового пользователя в вашем проекте Descope |
| `invite-user` | Приглашает нового пользователя в ваш проект Descope |

## Возможности

- Поиск и получение записей логов аудита
- Поиск и получение записей пользователей
- Создание новых пользователей
- Приглашение пользователей в проекты
- Интеграция с Management API Descope

## Переменные окружения

### Обязательные
- `DESCOPE_PROJECT_ID` - Ваш ID проекта Descope из app.descope.com/settings/project
- `DESCOPE_MANAGEMENT_KEY` - Ваш Management Key Descope из app.descope.com/settings/company/managementkeys

## Ресурсы

- [GitHub Repository](https://github.com/descope-sample-apps/descope-mcp-server)

## Примечания

Требует Node.js версии 18 или новее. Сервер может работать в режимах stdio или SSE. Для конфигурации необходим доступ к настройкам проекта Descope для получения ID проекта и Management Key.