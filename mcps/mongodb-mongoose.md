---
title: MongoDB & Mongoose MCP сервер
description: MCP сервер, который позволяет Claude взаимодействовать с базами данных MongoDB с опциональной поддержкой схем Mongoose для валидации и хуков.
tags:
- Database
- Storage
- API
- Integration
- DevOps
author: Community
featured: false
---

MCP сервер, который позволяет Claude взаимодействовать с базами данных MongoDB с опциональной поддержкой схем Mongoose для валидации и хуков.

## Установка

### NPX

```bash
npx -y mongo-mongoose-mcp
```

### Из исходников

```bash
# Clone the repository
git clone https://github.com/nabid-pf/mongo-mongoose-mcp.git
cd mongo-mongoose-mcp

# Install dependencies
npm install

# Build the project
npm run build

# Test with the MCP inspector
npx @modelcontextprotocol/inspector node dist/index.js
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "mongodb-mongoose": {
      "command": "npx",
      "args": [
        "-y", 
        "mongo-mongoose-mcp",
      ],
      "env": {
        "MONGODB_URI": "<your mongodb uri>",
        "SCHEMA_PATH" : "<path to the root folder of all your mongoose schema objects>"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `find` | Запрос документов с фильтрацией и проекцией |
| `listCollections` | Список доступных коллекций |
| `insertOne` | Вставка одного документа |
| `updateOne` | Обновление одного документа |
| `deleteOne` | Мягкое удаление одного документа |
| `count` | Подсчет документов с фильтрацией |
| `aggregate` | Запрос документов с пайплайном агрегации |
| `createIndex` | Создание нового индекса |
| `dropIndex` | Удаление индекса |
| `indexes` | Список индексов для коллекции |

## Возможности

- Запросы, агрегация, вставка, обновление и управление коллекциями MongoDB напрямую из Claude
- Опциональная поддержка схем Mongoose для валидации данных и хуков
- Реализация мягкого удаления для безопасности документов
- Четкое разделение между операциями со схемами и без схем

## Переменные окружения

### Обязательные
- `MONGODB_URI` - URI подключения к MongoDB

### Опциональные
- `SCHEMA_PATH` - Путь к корневой папке со всеми объектами схем mongoose

## Примеры использования

```
Show me all users in my database who are older than 30
```

```
Insert a new product with name 'Widget X', price $29.99, and category 'Electronics'
```

```
Count all completed orders from the past week
```

```
Create an index on the email field of the users collection
```

## Ресурсы

- [GitHub Repository](https://github.com/nabid-pf/mongo-mongoose-mcp)

## Примечания

Требует Node.js версии 18 или выше и MongoDB. Файлы схем Mongoose должны быть размещены в директории с именами файлов, отражающими названия коллекций. Использует нативный драйвер MongoDB для прямых операций и Mongoose для операций со схемами.