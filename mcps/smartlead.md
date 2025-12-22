---
title: Smartlead MCP сервер
description: MCP сервер, который предоставляет упрощённый интерфейс к Smartlead API,
  позволяя AI-ассистентам и инструментам автоматизации взаимодействовать с функциями email-маркетинга Smartlead, включая управление кампаниями, аналитику и отслеживание лидов.
tags:
- CRM
- Integration
- Analytics
- API
- Productivity
author: Community
featured: false
---

MCP сервер, который предоставляет упрощённый интерфейс к Smartlead API, позволяя AI-ассистентам и инструментам автоматизации взаимодействовать с функциями email-маркетинга Smartlead, включая управление кампаниями, аналитику и отслеживание лидов.

## Установка

### NPM

```bash
npm install smartlead-mcp-server@1.2.1
```

### NPX Direct

```bash
npx smartlead-mcp-server start
```

### Smithery

```bash
npx -y @smithery/cli install @jean-technologies/smartlead-mcp-server-local --client claude
```

### С n8n

```bash
npx smartlead-mcp-server sse
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "smartlead": {
      "command": "npx",
      "args": ["smartlead-mcp-server", "start"],
      "env": {
        "SMARTLEAD_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Настройка n8n

```json
1. Start the server: `npx smartlead-mcp-server sse`
2. Configure n8n MCP Client node with:
   - SSE URL: `http://localhost:3000/sse`
   - Message URL: `http://localhost:3000/message`
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `smartlead_download_campaign_data` | Скачать данные кампании с отслеживанием, поддерживая аналитику, лиды, последовательности или полный экспорт в JS... |
| `smartlead_view_download_statistics` | Просмотр статистики загрузок с фильтрацией по временному периоду (все, сегодня, неделя, месяц) и группировкой по ... |

## Возможности

- Управление кампаниями и лидами
- Статистика и аналитика
- Умная доставка и вебхуки
- Интеграция с n8n
- Управление клиентами
- Умные отправители
- Отслеживание загрузок и аналитика
- Множественные форматы экспорта (JSON, CSV)
- Отслеживание статистики загрузок

## Переменные окружения

### Обязательные
- `SMARTLEAD_API_KEY` - Ваш Smartlead API ключ для аутентификации

## Ресурсы

- [GitHub Repository](https://github.com/jean-technologies/smartlead-mcp-server-local)

## Примечания

Все функции теперь включены по умолчанию с максимальными разрешениями и не требуют лицензионного ключа. Загрузки отслеживаются в ~/.smartlead-mcp/downloads.json для аналитики. Выполните 'npx smartlead-mcp-server config' для интерактивной настройки учётных данных.