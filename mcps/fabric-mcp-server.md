---
title: fabric-mcp-server MCP сервер
description: Model Context Protocol сервер, который предоставляет паттерны Fabric от Дэниэла Миесслера в качестве инструментов для AI-агентов, позволяя выполнять паттерны с помощью ИИ для расширения возможностей ассистентов.
tags:
- AI
- Productivity
- Code
- Integration
- Analytics
author: Community
featured: false
---

Model Context Protocol сервер, который предоставляет паттерны Fabric от Дэниэла Миесслера в качестве инструментов для AI-агентов, позволяя выполнять паттерны с помощью ИИ для расширения возможностей ассистентов.

## Установка

### Из исходного кода

```bash
1. Clone the fabric-mcp-server repository
2. cd fabric-mcp-server
3. npm install
4. npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "fabric-mcp-server": {
      "command": "node",
      "args": [
        "<path-to-fabric-mcp-server>/build/index.js"
      ],
      "env": {}
    }
  }
}
```

### VS Code с Cline

```json
{
  "fabric-mcp-server": {
    "command": "node",
    "args": [
      "<path-to-fabric-mcp-server>/build/index.js"
    ],
    "env": {},
    "disabled": false,
    "autoApprove": [],
    "transportType": "stdio",
    "timeout": 60
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `analyze_claims` | Fabric паттерн для анализа утверждений |
| `summarize` | Fabric паттерн для создания резюме контента |
| `extract_wisdom` | Fabric паттерн для извлечения мудрости из контента |
| `create_mermaid_visualization` | Fabric паттерн для создания Mermaid визуализаций |

## Возможности

- Предоставление Fabric паттернов как инструментов - делает все Fabric паттерны доступными в качестве отдельных инструментов в MCP-совместимых AI-агентах
- Выполнение паттернов - пользователи могут выбирать и выполнять Fabric паттерны напрямую в задачах AI-ассистента
- Расширенные возможности - интегрирует выполнение паттернов с помощью ИИ для усиления функциональности AI-ассистентов
- Кроссплатформенная совместимость - работает с Claude Desktop, Cline и другими MCP-совместимыми AI-агентами

## Примеры использования

```
Simply mention that you'd like to use a Fabric pattern in your conversation
```

```
Ask Claude to list available patterns if you're unsure which one to use
```

```
Add 'use fabric-mcp-server' at the end of your prompts when using with Cline
```

## Ресурсы

- [GitHub Repository](https://github.com/adapoet/fabric-mcp-server)

## Примечания

Для пользователей Cline рекомендуется добавить правило в файл .clinerules для автоматического отображения списка Fabric паттернов и предложения выбора паттерна при создании новых задач. Полный список доступных паттернов можно найти в директории patterns репозитория Fabric.