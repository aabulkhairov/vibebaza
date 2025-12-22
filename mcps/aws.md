---
title: AWS MCP сервер
description: Реализация сервера Model Context Protocol для операций AWS, который поддерживает сервисы S3 и DynamoDB с автоматическим логированием операций и аудит-трейлом.
tags:
- Cloud
- Storage
- Database
- DevOps
- API
author: rishikavikondala
featured: true
install_command: npx -y @smithery/cli install mcp-server-aws --client claude
---

Реализация сервера Model Context Protocol для операций AWS, который поддерживает сервисы S3 и DynamoDB с автоматическим логированием операций и аудит-трейлом.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-server-aws --client claude
```

### Ручная установка

```bash
Clone repository and add to claude_desktop_config.json with uv command
```

## Конфигурация

### Claude Desktop

```json
"mcpServers": {
  "mcp-server-aws": {
    "command": "uv",
    "args": [
      "--directory",
      "/path/to/repo/mcp-server-aws",
      "run",
      "mcp-server-aws"
    ]
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `s3_bucket_create` | Создать новый S3 бакет |
| `s3_bucket_list` | Список всех S3 бакетов |
| `s3_bucket_delete` | Удалить S3 бакет |
| `s3_object_upload` | Загрузить объект в S3 |
| `s3_object_delete` | Удалить объект из S3 |
| `s3_object_list` | Список объектов в S3 бакете |
| `s3_object_read` | Прочитать содержимое объекта из S3 |
| `dynamodb_table_create` | Создать новую таблицу DynamoDB |
| `dynamodb_table_describe` | Получить детали о таблице DynamoDB |
| `dynamodb_table_delete` | Удалить таблицу DynamoDB |
| `dynamodb_table_update` | Обновить таблицу DynamoDB |
| `dynamodb_item_put` | Добавить элемент в таблицу DynamoDB |
| `dynamodb_item_get` | Получить элемент из таблицы DynamoDB |
| `dynamodb_item_update` | Обновить элемент в таблице DynamoDB |
| `dynamodb_item_delete` | Удалить элемент из таблицы DynamoDB |

## Возможности

- Операции с S3 бакетами и объектами
- Управление таблицами DynamoDB и операции с элементами
- Batch операции для DynamoDB
- Управление TTL для таблиц DynamoDB
- Автоматическое логирование операций
- Аудит-трейл доступен через ресурс audit://aws-operations

## Переменные окружения

### Обязательные
- `AWS_ACCESS_KEY_ID` - Ключ доступа AWS для аутентификации
- `AWS_SECRET_ACCESS_KEY` - Секретный ключ доступа AWS для аутентификации

### Опциональные
- `AWS_REGION` - Регион AWS (по умолчанию us-east-1)

## Примеры использования

```
create an S3 bucket and give it a random name
```

## Ресурсы

- [GitHub Repository](https://github.com/rishikavikondala/mcp-server-aws)

## Примечания

Требует IAM пользователя с правами чтения/записи для S3 и DynamoDB. Также можно использовать стандартную цепочку учетных данных AWS, настроенную через AWS CLI. Указан как Community Server в репозитории MCP серверов.