---
title: EdgeOne Pages MCP сервер
description: MCP сервис для развертывания HTML контента, папок или full-stack проектов на EdgeOne Pages с получением публично доступных URL через edge доставку.
tags:
- Cloud
- DevOps
- Storage
- Integration
- API
author: Community
featured: false
---

MCP сервис для развертывания HTML контента, папок или full-stack проектов на EdgeOne Pages с получением публично доступных URL через edge доставку.

## Установка

### NPX (Полнофункциональная версия)

```bash
npx edgeone-pages-mcp-fullstack@latest
```

### NPX (Устаревшая версия)

```bash
npx edgeone-pages-mcp@latest
```

## Конфигурация

### Полнофункциональный MCP сервер (Международный)

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "timeout": 600,
      "command": "npx",
      "args": ["edgeone-pages-mcp-fullstack@latest"]
    }
  }
}
```

### Полнофункциональный MCP сервер (Китай)

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "timeout": 600,
      "command": "npx",
      "args": ["edgeone-pages-mcp-fullstack@latest", "--region", "china"]
    }
  }
}
```

### Устаревший MCP сервер

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "command": "npx",
      "args": ["edgeone-pages-mcp@latest"],
      "env": {
        "EDGEONE_PAGES_API_TOKEN": "",
        "EDGEONE_PAGES_PROJECT_NAME": ""
      }
    }
  }
}
```

### Потоковый HTTP MCP сервер

```json
{
  "mcpServers": {
    "edgeone-pages-mcp-server": {
      "url": "https://mcp-on-edge.edgeone.site/mcp-server"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `deploy_html` | Разворачивает HTML контент на EdgeOne Pages и возвращает публично доступный URL с edge доставкой |
| `deploy_folder` | Разворачивает полные проекты, включая статические сайты и full-stack приложения на EdgeOne Pages |
| `deploy_folder_or_zip` | Устаревший инструмент для развертывания папок или zip файлов в проекты EdgeOne Pages |

## Возможности

- Развертывание HTML контента с автоматическим созданием публичного URL
- Развертывание полных проектов статических сайтов
- Развертывание full-stack приложений
- Edge доставка с быстрым глобальным доступом
- Интеграция с EdgeOne Pages Functions и KV хранилищем
- Поддержка создания новых проектов и обновления существующих
- Комплексная обработка ошибок API и обратная связь
- Множественные методы развертывания (stdio, HTTP потоковый)
- Поддержка международных регионов Tencent Cloud и Китая

## Переменные окружения

### Опциональные
- `EDGEONE_PAGES_API_TOKEN` - API токен EdgeOne Pages для развертывания папок или zip файлов
- `EDGEONE_PAGES_PROJECT_NAME` - Имя проекта для обновления существующего проекта (оставьте пустым для создания нового)

## Примеры использования

```
Deploy this HTML page to a public URL
```

```
Deploy my website folder to EdgeOne Pages
```

```
Create a publicly accessible deployment of this full-stack project
```

## Ресурсы

- [GitHub Repository](https://github.com/TencentEdgeOne/edgeone-pages-mcp)

## Примечания

Требуется Node.js 18 или выше. Устаревший MCP сервер скоро будет упразднен. Open source с возможностью самостоятельного развертывания. Архитектура использует EdgeOne Pages Functions для serverless вычислений и KV хранилище для быстрого edge доступа.