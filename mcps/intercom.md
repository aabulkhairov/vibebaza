---
title: Intercom MCP сервер
description: MCP-совместимый сервер, который позволяет AI-ассистентам получать доступ и анализировать данные службы поддержки клиентов из Intercom, включая разговоры и тикеты с расширенными возможностями фильтрации.
tags:
- CRM
- API
- Integration
- Analytics
- Productivity
author: raoulbia-ai
featured: false
---

MCP-совместимый сервер, который позволяет AI-ассистентам получать доступ и анализировать данные службы поддержки клиентов из Intercom, включая разговоры и тикеты с расширенными возможностями фильтрации.

## Установка

### NPM

```bash
npm install -g mcp-server-for-intercom
export INTERCOM_ACCESS_TOKEN="your_token_here"
intercom-mcp
```

### Docker

```bash
docker build -t mcp-intercom .
docker run --rm -it -p 3000:3000 -p 8080:8080 -e INTERCOM_ACCESS_TOKEN="your_token_here" mcp-intercom:latest
```

### Docker Standard

```bash
docker build -t mcp-intercom-standard -f Dockerfile.standard .
docker run --rm -it -p 3000:3000 -p 8080:8080 -e INTERCOM_ACCESS_TOKEN="your_token_here" mcp-intercom-standard:latest
```

### Из исходного кода

```bash
git clone https://github.com/raoulbia-ai/mcp-server-for-intercom.git
cd mcp-server-for-intercom
npm install
npm run build
npm run dev
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "intercom-mcp": {
      "command": "intercom-mcp",
      "args": [],
      "env": {
        "INTERCOM_ACCESS_TOKEN": "your_intercom_api_token"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `list_conversations` | Получает все разговоры в указанном диапазоне дат с фильтрацией контента по ключевым словам и исключениям ... |
| `search_conversations_by_customer` | Находит разговоры для конкретного клиента по email или Intercom ID, с опциональным диапазоном дат и... |
| `search_tickets_by_status` | Получает тикеты по их статусу (открытые, ожидающие или решенные) с опциональной фильтрацией по датам |
| `search_tickets_by_customer` | Находит тикеты, связанные с конкретным клиентом по email или Intercom ID с опциональным диапазоном дат... |

## Возможности

- Поиск разговоров и тикетов с расширенной фильтрацией
- Фильтрация по клиенту, статусу, диапазону дат и ключевым словам
- Поиск по содержимому email даже когда контакт не существует
- Эффективная серверная фильтрация через Intercom API поиска
- Бесшовная интеграция с MCP-совместимыми AI-ассистентами

## Переменные окружения

### Обязательные
- `INTERCOM_ACCESS_TOKEN` - Ваш Intercom API токен (доступен в настройках вашего Intercom аккаунта)

## Ресурсы

- [GitHub Repository](https://github.com/raoulbia-ai/mcp-server-for-intercom)

## Примечания

Диапазон дат для разговоров не должен превышать 7 дней. Сервер может определять ID контактов по email для эффективного поиска и находить разговоры по содержимому email даже если контакт не существует. Стандартная Docker конфигурация оптимизирована для совместимости с Glama. Этот проект независим и не связан с Intercom Inc.