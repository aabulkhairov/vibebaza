---
title: AWS Athena MCP сервер
description: Model Context Protocol (MCP) сервер для выполнения запросов AWS Athena, позволяющий AI-ассистентам выполнять SQL-запросы к базам данных AWS Athena и получать результаты.
tags:
- Database
- Cloud
- Analytics
- API
author: lishenxydlgzs
featured: false
---

Model Context Protocol (MCP) сервер для выполнения запросов AWS Athena, позволяющий AI-ассистентам выполнять SQL-запросы к базам данных AWS Athena и получать результаты.

## Установка

### NPX

```bash
npx -y @lishenxydlgzs/aws-athena-mcp
```

## Конфигурация

### Конфигурация MCP

```json
{
  "mcpServers": {
    "athena": {
      "command": "npx",
      "args": ["-y", "@lishenxydlgzs/aws-athena-mcp"],
      "env": {
        // Required
        "OUTPUT_S3_PATH": "s3://your-bucket/athena-results/",
        
        // Optional AWS configuration
        "AWS_REGION": "us-east-1",
        "AWS_PROFILE": "default",
        "AWS_ACCESS_KEY_ID": "",
        "AWS_SECRET_ACCESS_KEY": "",
        "AWS_SESSION_TOKEN": "",
        
        // Optional server configuration
        "ATHENA_WORKGROUP": "default_workgroup",
        "QUERY_TIMEOUT_MS": "300000",
        "MAX_RETRIES": "100",
        "RETRY_DELAY_MS": "500"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `run_query` | Выполнение SQL-запроса с помощью AWS Athena с параметрами для базы данных, запроса и максимального количества строк |
| `get_status` | Проверка статуса выполнения запроса по queryExecutionId |
| `get_result` | Получение результатов завершенного запроса по queryExecutionId |
| `list_saved_queries` | Список всех сохраненных (именованных) запросов в Athena |
| `run_saved_query` | Выполнение ранее сохраненного запроса по его ID с опциональной заменой базы данных |

## Возможности

- Выполнение SQL-запросов к базам данных AWS Athena
- Получение результатов запросов с настраиваемым лимитом строк (до 10,000)
- Проверка статуса выполнения запросов и статистики
- Обработка долго выполняющихся запросов с механизмами таймаута и повторных попыток
- Управление сохраненными запросами в рабочих группах Athena
- Поддержка нескольких методов аутентификации AWS

## Переменные окружения

### Обязательные
- `OUTPUT_S3_PATH` - Путь к S3 bucket для хранения результатов запросов Athena

### Опциональные
- `AWS_REGION` - Регион AWS для операций Athena
- `AWS_PROFILE` - Профиль AWS CLI для использования
- `AWS_ACCESS_KEY_ID` - ID ключа доступа AWS для аутентификации
- `AWS_SECRET_ACCESS_KEY` - Секретный ключ доступа AWS для аутентификации
- `AWS_SESSION_TOKEN` - Токен сессии AWS для временных учетных данных
- `ATHENA_WORKGROUP` - Рабочая группа Athena для выполнения запросов
- `QUERY_TIMEOUT_MS` - Таймаут запроса в миллисекундах (по умолчанию: 300000ms)
- `MAX_RETRIES` - Максимальное количество попыток повтора (по умолчанию: 100)

## Примеры использования

```
List all databases in Athena
```

```
Show me all tables in the default database
```

```
What's the schema of the asin_sitebestimg table?
```

```
Show some rows from my_database.mytable
```

```
Find the average price by category for in-stock products
```

## Ресурсы

- [GitHub Repository](https://github.com/lishenxydlgzs/aws-athena-mcp)

## Примечания

Требует Node.js >= 16, учетные данные AWS с соответствующими разрешениями для Athena и S3, а также S3 bucket для результатов запросов. Поддерживает конфигурацию AWS CLI, переменные окружения и IAM роли для аутентификации.