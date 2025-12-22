---
title: Mandoline MCP сервер
description: Позволяет AI-ассистентам, таким как Claude, Cursor и другим, анализировать, критически оценивать и постоянно улучшать собственную производительность с помощью фреймворка оценки Mandoline через Model Context Protocol.
tags:
- AI
- Analytics
- Productivity
- API
- Integration
author: Community
featured: false
install_command: 'claude mcp add --scope user --transport http mandoline https://mandoline.ai/mcp
  --header "x-api-key: sk_****"'
---

Позволяет AI-ассистентам, таким как Claude, Cursor и другим, анализировать, критически оценивать и постоянно улучшать собственную производительность с помощью фреймворка оценки Mandoline через Model Context Protocol.

## Установка

### Размещенный сервер (Claude Code)

```bash
claude mcp add --scope user --transport http mandoline https://mandoline.ai/mcp --header "x-api-key: sk_****"
```

### Размещенный сервер (Codex)

```bash
codex mcp add mandoline --env MANDOLINE_API_KEY=sk_**** -- npx -y mcp-remote https://mandoline.ai/mcp --header 'x-api-key: ${MANDOLINE_API_KEY}'
```

### Из исходного кода

```bash
git clone https://github.com/mandoline-ai/mandoline-mcp-server.git
cd mandoline-mcp-server
npm install
npm run build
npm start
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "Mandoline": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mandoline.ai/mcp",
        "--header",
        "x-api-key: ${MANDOLINE_API_KEY}"
      ],
      "env": {
        "MANDOLINE_API_KEY": "sk_****"
      }
    }
  }
}
```

### Cursor

```json
{
  "mcpServers": {
    "Mandoline": {
      "url": "https://mandoline.ai/mcp",
      "headers": {
        "x-api-key": "sk_****"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_server_health` | Подтверждает доступность MCP сервера и возврат корректного статуса |
| `create_metric` | Определяет пользовательские критерии оценки для ваших конкретных задач |
| `batch_create_metrics` | Создает несколько метрик оценки за одну операцию |
| `get_metric` | Получает детали о конкретной метрике |
| `get_metrics` | Просматривает ваши метрики с фильтрацией и пагинацией |
| `update_metric` | Изменяет существующие определения метрик |
| `create_evaluation` | Оценивает пары промпт/ответ по вашим метрикам |
| `batch_create_evaluations` | Оценивает одно и то же содержимое по нескольким метрикам |
| `get_evaluation` | Получает результаты и оценки анализа |
| `get_evaluations` | Просматривает историю оценок с фильтрацией и пагинацией |
| `update_evaluation` | Добавляет метаданные или контекст к оценкам |

## Возможности

- Позволяет AI-ассистентам анализировать и критически оценивать собственную производительность
- Непрерывное улучшение через фреймворк оценки
- Создание и управление пользовательскими метриками оценки
- Пакетные операции оценки для эффективности
- Оценка пар промпт/ответ по определенным метрикам
- Просмотр истории оценок с фильтрацией и пагинацией
- Мониторинг состояния и проверка статуса

## Переменные окружения

### Обязательные
- `MANDOLINE_API_KEY` - API ключ с mandoline.ai/account для аутентификации

### Опциональные
- `PORT` - Порт для локального сервера (по умолчанию 8080)
- `LOG_LEVEL` - Конфигурация уровня логирования

## Ресурсы

- [GitHub Repository](https://github.com/mandoline-ai/mandoline-mcp-server)

## Примечания

Большинству пользователей следует использовать размещенный сервер по адресу https://mandoline.ai/mcp вместо локального запуска. Перезапустите ваш AI-ассистент после изменения конфигурации. Требуется API ключ с mandoline.ai/account.