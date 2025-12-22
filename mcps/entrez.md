---
title: Entrez MCP сервер
description: Комплексный MCP сервер, предоставляющий доступ к API NCBI, включая E-utilities, PubChem и PMC сервисы для данных биомедицинских исследований.
tags:
- Database
- API
- Search
- Analytics
author: Community
featured: false
---

Комплексный MCP сервер, предоставляющий доступ к API NCBI, включая E-utilities, PubChem и PMC сервисы для данных биомедицинских исследований.

## Установка

### Из исходного кода

```bash
git clone <this-repo>
cd entrez-mcp-server
npm install
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "calculator": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "http://localhost:8787/mcp"  // or remote-mcp-server-authless.your-account.workers.dev/mcp
      ]
    }
  }
}
```

## Возможности

- Полное покрытие NCBI API: E-utilities, PubChem PUG, PMC API
- Не требует настройки: Работает сразу без какой-либо конфигурации
- Опциональное повышение производительности: Добавьте свой бесплатный NCBI API ключ для трёхкратного улучшения лимитов запросов
- Ограничение скорости: Встроенное соблюдение лимитов NCBI (3/сек → 10/сек с API ключом)
- Удобство использования: Разработан как для технических, так и для нетехнических пользователей

## Переменные окружения

### Опциональные
- `NCBI_API_KEY` - Опциональный NCBI API ключ для улучшенных лимитов запросов (10 запросов/секунда против 3 запросов/секунда)

## Ресурсы

- [GitHub Repository](https://github.com/QuentinCody/entrez-mcp-server)

## Примечания

Сервер поддерживает деплой на Cloudflare Workers и может быть подключен как к Cloudflare AI Playground, так и к Claude Desktop. Тестирование производительности доступно через 'node test-rate-limits.js'. Для Cloudflare Code Mode используйте идентификаторы инструментов с подчёркиваниями вместо дефисов, чтобы избежать проблем с синтаксисом JavaScript.