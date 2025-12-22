---
title: Raygun MCP сервер
description: Удалённый MCP сервер, который подключает AI-ассистентов к данным отчётов о крашах и мониторинга пользователей Raygun через естественные языковые разговоры.
tags:
- Monitoring
- DevOps
- Analytics
- API
- Integration
author: MindscapeHQ
featured: false
---

Удалённый MCP сервер, который подключает AI-ассистентов к данным отчётов о крашах и мониторинга пользователей Raygun через естественные языковые разговоры.

## Установка

### Amp

```bash
amp mcp add raygun --header "Authorization=Bearer YOUR_PAT_TOKEN" https://api.raygun.com/v3/mcp
```

### Claude Code

```bash
claude mcp add --transport http raygun https://api.raygun.com/v3/mcp --header "Authorization: Bearer YOUR_PAT_TOKEN"
```

### Gemini CLI

```bash
gemini mcp add --transport http raygun https://api.raygun.com/v3/mcp --header "Authorization: Bearer YOUR_PAT_TOKEN"
```

## Конфигурация

### Codex

```json
[mcp_servers.raygun]
command = "npx"
args = ["mcp-remote", "https://api.raygun.com/v3/mcp", "--header", "Authorization: Bearer YOUR_PAT_TOKEN"]
```

### Cursor

```json
{
  "mcpServers": {
    "Raygun": {
      "url": "https://api.raygun.com/v3/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_PAT_TOKEN"
      }
    }
  }
}
```

### JetBrains AI Assistant

```json
{
  "mcpServers": {
    "Raygun": {
      "url": "https://api.raygun.com/v3/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_PAT_TOKEN"
      }
    }
  }
}
```

### VS Code

```json
{
  "servers": {
    "raygun": {
      "url": "https://api.raygun.com/v3/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_PAT_TOKEN"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `applications_list` | Список всех приложений в вашем аккаунте Raygun |
| `applications_search` | Поиск приложений по имени |
| `application_get_details` | Получение детальной информации о приложении |
| `application_regenerate_api_key` | Генерация нового API ключа для приложения |
| `error_groups_list` | Список групп ошибок в приложении |
| `error_group_investigate` | Получение полных деталей о конкретной группе ошибок |
| `error_group_update_status` | Изменение статуса группы ошибок (решено, игнорировано, активно) |
| `error_group_add_comment` | Добавление заметок расследования к группе ошибок |
| `error_instances_browse` | Просмотр отдельных случаев ошибок |
| `error_instance_get_details` | Получение полного стек-трейса и контекста для экземпляра ошибки |
| `deployments_list` | Список деплоев для приложения |
| `deployment_create` | Создание новой записи деплоя |
| `deployment_get_latest` | Получение самого последнего деплоя с анализом ошибок |
| `deployment_investigate` | Получение подробной информации о деплое |
| `deployment_manage` | Обновление или удаление деплоя |

## Возможности

- Управление ошибками - Расследование, решение и отслеживание ошибок и крашей приложений с полными стек-трейсами и контекстом
- Отслеживание деплоев - Мониторинг релизов и корреляция ошибок с деплоями для выявления проблемных изменений
- Анализ производительности - Анализ времени загрузки страниц, пользовательских метрик и трендов производительности во времени
- Мониторинг пользователей - Отслеживание пользовательских сессий, паттернов поведения и выявление затронутых пользователей
- Командное сотрудничество - Управление приглашениями и координация решения ошибок в вашей команде
- Метрики и аналитика - Анализ временных рядов и гистограммы распределения для ошибок и производительности

## Примеры использования

```
Покажи мне самые последние группы ошибок в моих Raygun приложениях
```

```
Какие были последние деплои и привнесли ли они новые ошибки?
```

```
Проанализируй тренды производительности для моих топовых страниц за последние 7 дней
```

## Ресурсы

- [GitHub Repository](https://github.com/MindscapeHQ/mcp-server-raygun)

## Примечания

Это удалённый MCP сервер, размещённый по адресу https://api.raygun.com/v3/mcp. Требует персональный токен доступа Raygun (PAT), который можно получить на https://app.raygun.com/user/tokens. Сервер требует активную подписку Raygun.