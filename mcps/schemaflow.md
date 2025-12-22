---
title: SchemaFlow MCP сервер
description: Доступ к схеме базы данных PostgreSQL и Supabase в реальном времени для AI-IDE через Model Context Protocol. Предоставляет контекст живой базы данных через безопасные SSE соединения для более умной генерации кода.
tags:
- Database
- AI
- Productivity
- API
- Integration
author: CryptoRadi
featured: false
---

Доступ к схеме базы данных PostgreSQL и Supabase в реальном времени для AI-IDE через Model Context Protocol. Предоставляет контекст живой базы данных через безопасные SSE соединения для более умной генерации кода.

## Конфигурация

### Cursor IDE

```json
{
  "name": "schemaflow",
  "type": "sse",
  "url": "https://api.schemaflow.dev/mcp/?token=your-token-here"
}
```

### Windsurf IDE

```json
{
  "mcpServers": {
    "schemaflow": {
      "type": "sse",
      "url": "https://api.schemaflow.dev/mcp/?token=your-token-here"
    }
  }
}
```

### VS Code + Cline

```json
{
  "mcpServers": {
    "schemaflow": {
      "type": "sse", 
      "url": "https://api.schemaflow.dev/mcp/?token=your-token-here"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_schema` | Получает полную информацию о схеме базы данных, включая таблицы, колонки, связи, функции... |
| `analyze_database` | Выполняет комплексный анализ базы данных, включая анализ производительности, оценку безопасности и... |
| `check_schema_alignment` | Проверяет вашу схему PostgreSQL или Supabase на соответствие лучшим практикам и выявляет потенциальные проблемы... |

## Возможности

- Доступ к схеме PostgreSQL и Supabase в реальном времени
- Кеширование схемы для производительности
- Безопасная аутентификация на основе токенов
- Интерактивная визуализация схемы
- Экспорт в нескольких форматах (JSON, Markdown, SQL, Mermaid)
- Анализ производительности и советы по оптимизации
- Нативная интеграция с Supabase
- Валидация схемы в соответствии с лучшими практиками

## Примеры использования

```
Show me my database schema
```

```
What tables do I have?
```

```
Show me all relationships
```

```
List database functions
```

```
Analyze my database performance
```

## Ресурсы

- [GitHub Repository](https://github.com/CryptoRadi/schemaflow-mcp-server)

## Примечания

Требует посещения SchemaFlow Dashboard для подключения базы данных, кеширования схемы и генерации MCP токена. Используются только метаданные схемы - фактические данные не читаются и не сохраняются. Часть более крупной платформы SchemaFlow с дополнительными возможностями визуализации и экспорта.