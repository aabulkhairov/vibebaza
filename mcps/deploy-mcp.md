---
title: deploy-mcp MCP сервер
description: Универсальный трекер деплоя, который отслеживает развертывания на нескольких платформах (Vercel, Netlify, Cloudflare Pages) прямо в разговорах с ИИ, с обновлениями статуса в реальном времени и значками деплоя.
tags:
- DevOps
- Monitoring
- Cloud
- Integration
- Productivity
author: alexpota
featured: false
---

Универсальный трекер деплоя, который отслеживает развертывания на нескольких платформах (Vercel, Netlify, Cloudflare Pages) прямо в разговорах с ИИ, с обновлениями статуса в реальном времени и значками деплоя.

## Установка

### NPX (Быстрый старт)

```bash
npx deploy-mcp
```

### Глобальная установка

```bash
npm install -g deploy-mcp
deploy-mcp
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "deploy-mcp": {
      "command": "npx",
      "args": ["-y", "deploy-mcp"],
      "env": {
        "VERCEL_TOKEN": "your-vercel-token",
        "NETLIFY_TOKEN": "your-netlify-token",
        "CLOUDFLARE_TOKEN": "accountId:globalApiKey"
      }
    }
  }
}
```

### Continue.dev

```json
{
  "experimental": {
    "modelContextProtocolServer": {
      "transport": {
        "type": "stdio",
        "command": "npx",
        "args": ["-y", "deploy-mcp"]
      },
      "env": {
        "VERCEL_TOKEN": "your-vercel-token",
        "NETLIFY_TOKEN": "your-netlify-token"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `check_deployment_status` | Получить последний статус деплоя или историю |
| `watch_deployment` | Мониторить деплой в реальном времени |
| `compare_deployments` | Сравнить последние деплои |
| `get_deployment_logs` | Получить логи деплоя |
| `list_projects` | Список всех доступных проектов |

## Возможности

- Отслеживание деплоев на нескольких платформах (Vercel, Netlify, Cloudflare Pages)
- Мониторинг деплоя в реальном времени
- Живые значки статуса деплоя для репозиториев
- История и сравнение деплоев
- Доступ к логам деплоя
- Обнаружение проектов/сайтов на разных платформах
- Поддержка webhook для обновления значков в реальном времени
- Никакой телеметрии или сбора данных
- Хранение токенов только локально

## Переменные окружения

### Опциональные
- `VERCEL_TOKEN` - API токен для доступа к деплоям Vercel
- `NETLIFY_TOKEN` - Персональный токен доступа для сайтов и деплоев Netlify
- `CLOUDFLARE_TOKEN` - API токен или accountId:globalApiKey для Cloudflare Pages

## Примеры использования

```
Check my Vercel deployment for project-name
```

```
What's the status of my latest Netlify deployment?
```

```
Show me deployment logs
```

```
Watch my deployment progress
```

```
List all my Vercel projects
```

## Ресурсы

- [GitHub Repository](https://github.com/alexpota/deploy-mcp)

## Примечания

Поддерживает одновременное отслеживание нескольких платформ при предоставлении токенов для каждой. Включает значки статуса деплоя, которые можно встроить в README файлы через endpoints shields.io. Поддержка GitHub Pages появится в ближайшее время.