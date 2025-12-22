---
title: DataCite MCP сервер
description: MCP сервер, который предоставляет доступ к GraphQL API DataCite для запроса богатых метаданных о научных работах, включая DOI, наборы данных, программное обеспечение, публикации и их связи в рамках PID Graph.
tags:
- API
- Database
- Search
- Analytics
- Integration
author: QuentinCody
featured: false
---

MCP сервер, который предоставляет доступ к GraphQL API DataCite для запроса богатых метаданных о научных работах, включая DOI, наборы данных, программное обеспечение, публикации и их связи в рамках PID Graph.

## Установка

### MCP Remote

```bash
npx mcp-remote https://datacite-mcp-server.quentincody.workers.dev/mcp
```

### Из исходного кода

```bash
git clone https://github.com/yourusername/datacite-mcp-server.git
cd datacite-mcp-server
npm install
npm run dev
```

### Деплой на Cloudflare Workers

```bash
npx wrangler deploy
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "datacite": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://datacite-mcp-server.quentincody.workers.dev/mcp"
      ]
    }
  }
}
```

## Возможности

- Доступ к DataCite GraphQL API через MCP
- Запрос метаданных о научных работах, наборах данных, публикациях и многом другом
- Исследование связей между научными результатами, исследователями, фондами и организациями
- Построен на Cloudflare Workers для надежного хостинга
- Совместим с Cloudflare AI Playground
- Доступен устаревший транспорт Server-Sent Events по адресу /sse

## Переменные окружения

### Опциональные
- `MCP_ALLOWED_ORIGINS` - Список дополнительных источников для авторизации запросов, разделенный запятыми (включите буквальное 'null' для изолированных клиентов)

## Примеры использования

```
Используйте DataCite API для поиска недавних наборов данных об изменении климата
```

```
Запросите DataCite API для публикаций, финансируемых Европейским исследовательским советом
```

```
Найдите наборы данных, связанные с COVID-19, за 2020 год
```

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/datacite-mcp-server)

## Примечания

Этот проект доступен под лицензией MIT с требованием академического цитирования. Академическое/исследовательское использование требует правильного цитирования, в то время как коммерческое/неакадемическое использование следует стандартным условиям лицензии MIT. Сервер обеспечивает соблюдение рекомендаций по безопасности MCP транспорта путем валидации заголовка Origin в запросах. Локальный сервер разработки запускается по адресу http://localhost:8787/mcp.