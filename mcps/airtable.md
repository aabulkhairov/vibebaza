---
title: Airtable MCP сервер
description: Model Context Protocol сервер с инструментами для работы с Airtable API.
  Программное управление базами, таблицами, полями и записями со специализированными
  возможностями staged table building.
tags:
- Database
- Productivity
- CRM
- API
- Integration
author: felores
featured: false
---

Model Context Protocol сервер с инструментами для работы с Airtable API. Программное управление базами, таблицами, полями и записями со специализированными возможностями staged table building.

## Установка

### NPX (рекомендуется)

```bash
npx @felores/airtable-mcp-server
```

### MCP Installer

```bash
Install @felores/airtable-mcp-server set the environment variable AIRTABLE_API_KEY to 'your_api_key'
```

### Из исходников

```bash
git clone https://github.com/felores/airtable-mcp.git
cd airtable-mcp
npm install
npm run build
node build/index.js
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["@felores/airtable-mcp-server"],
      "env": {
        "AIRTABLE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "mcpServers": {
    "airtable": {
      "command": "node",
      "args": ["path/to/airtable-mcp/build/index.js"],
      "env": {
        "AIRTABLE_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `list_bases` | Список всех доступных баз Airtable |
| `list_tables` | Список всех таблиц в базе |
| `create_table` | Создание новой таблицы с полями |
| `update_table` | Обновление имени или описания таблицы |
| `create_field` | Добавление нового поля в таблицу |
| `update_field` | Изменение существующего поля |
| `list_records` | Получение записей из таблицы |
| `create_record` | Добавление новой записи |
| `update_record` | Изменение существующей записи |
| `delete_record` | Удаление записи |
| `search_records` | Поиск записей по критериям |
| `get_record` | Получение одной записи по ID |

## Возможности

- Специализированная staged table building имплементация для минимизации ошибок
- Полное управление базами и таблицами
- Полное управление полями с множеством типов (text, email, phone, number, currency, date, select options)
- Комплексные CRUD операции с записями и поиск
- Множество цветов для select полей
- System prompt и project knowledge файлы для улучшенного LLM guidance

## Переменные окружения

### Обязательные
- `AIRTABLE_API_KEY` — персональный access token из Airtable с нужными scopes (data.records:read/write, schema.bases:read/write)

## Примеры использования

```
List all bases
```

```
Create a new table with fields
```

```
Add records to a table
```

```
Search for records matching specific criteria
```

## Ресурсы

- [GitHub Repository](https://github.com/felores/airtable-mcp)

## Примечания

Требуется Node.js версии 18 или выше. Airtable API key нужно получить в Airtable Builder Hub со специфическими scopes: data.records:read, data.records:write, schema.bases:read, schema.bases:write. Включает специализированные system prompts для лучшей интеграции с Claude Desktop.
