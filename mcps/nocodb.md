---
title: NocoDB MCP сервер
description: MCP сервер на TypeScript, который обеспечивает удобное взаимодействие с базами данных NocoDB через команды на естественном языке, предоставляя CRUD операции для таблиц и загрузку файлов.
tags:
- Database
- API
- Integration
- Productivity
- Storage
author: edwinbernadus
featured: false
---

MCP сервер на TypeScript, который обеспечивает удобное взаимодействие с базами данных NocoDB через команды на естественном языке, предоставляя CRUD операции для таблиц и загрузку файлов.

## Установка

### Из исходников

```bash
npm install
npm run build
```

### Прямой вызов через NPX

```bash
npx -y nocodb-mcp-server {NOCODB_URL} {NOCODB_BASE_ID} {NOCODB_API_TOKEN}
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "nocodb": {
      "command": "node",
      "args": ["{working_folder}/dist/start.js"],
      "env": {
        "NOCODB_URL": "https://your-nocodb-instance.com",
        "NOCODB_BASE_ID": "your_base_id_here",
        "NOCODB_API_TOKEN": "your_api_token_here"
      }
    }
  }
}
```

## Возможности

- CRUD операции с таблицами NocoDB через команды на естественном языке
- Загрузка файлов для создания таблиц из JSON данных
- Массовое создание и удаление записей
- Динамическое добавление и удаление колонок
- Обновление записей с помощью команд на естественном языке
- Реализация на TypeScript для улучшенной поддерживаемости

## Переменные окружения

### Обязательные
- `NOCODB_URL` - URL вашего экземпляра NocoDB
- `NOCODB_API_TOKEN` - Ваш API токен NocoDB для аутентификации
- `NOCODB_BASE_ID` - ID базы вашей базы данных NocoDB (находится в URL)

## Примеры использования

```
get data from nocodb, table: Shinobi
```

```
add new row, with name: sasuke-2
```

```
update all rows, remove suffix -
```

```
delete all rows with name naruto
```

```
add column with name: Age
```

## Ресурсы

- [GitHub Repository](https://github.com/edwinbernadus/nocodb-mcp-server)

## Примечания

Это форк оригинального NocoDB-MCP-Server на TypeScript с улучшенной поддерживаемостью. Для подробной информации об API функциях обратитесь к API_FUNCTION.md. NOCODB_BASE_ID можно найти в URL вашего NocoDB в следующем формате: https://app.nocodb.com/#{USERNAME}/{NOCODB_BASE_ID}/{TABLE_ID}. Используйте https://app.nocodb.com в качестве NOCODB_URL, если используете облачную версию NocoDB.