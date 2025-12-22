---
title: AWS Resources Operations MCP сервер
description: MCP сервер, который позволяет выполнять Python код для запроса или модификации любых AWS ресурсов через boto3, предоставляя полные возможности управления AWS операциями.
tags:
- Cloud
- DevOps
- API
- Integration
- Security
author: baryhuang
featured: false
install_command: npx -y @smithery/cli install mcp-server-aws-resources-python --client
  claude
---

MCP сервер, который позволяет выполнять Python код для запроса или модификации любых AWS ресурсов через boto3, предоставляя полные возможности управления AWS операциями.

## Установка

### Smithery

```bash
npx -y @smithery/cli install mcp-server-aws-resources-python --client claude
```

### Docker Hub

```bash
docker pull buryhuang/mcp-server-aws-resources:latest
```

### Docker Build

```bash
docker build -t mcp-server-aws-resources .
```

### Docker Run с учетными данными

```bash
docker run \
  -e AWS_ACCESS_KEY_ID=your_access_key_id_here \
  -e AWS_SECRET_ACCESS_KEY=your_secret_access_key_here \
  -e AWS_DEFAULT_REGION=your_AWS_DEFAULT_REGION \
  buryhuang/mcp-server-aws-resources:latest
```

### Docker Run с профилем

```bash
docker run \
  -e AWS_PROFILE=[AWS_PROFILE_NAME] \
  -v ~/.aws:/root/.aws \
  buryhuang/mcp-server-aws-resources:latest
```

## Конфигурация

### Claude Desktop - Docker с учетными данными

```json
{
  "mcpServers": {
    "aws-resources": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "AWS_ACCESS_KEY_ID=your_access_key_id_here",
        "-e",
        "AWS_SECRET_ACCESS_KEY=your_secret_access_key_here",
        "-e",
        "AWS_DEFAULT_REGION=us-east-1",
        "buryhuang/mcp-server-aws-resources:latest"
      ]
    }
  }
}
```

### Claude Desktop - Docker с профилем

```json
{
  "mcpServers": {
    "aws-resources": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "AWS_PROFILE=default",
        "-v",
        "~/.aws:/root/.aws",
        "buryhuang/mcp-server-aws-resources:latest"
      ]
    }
  }
}
```

### Claude Desktop - Git Clone

```json
{
  "mcpServers": {
    "aws": {
      "command": "/Users/gmr/.local/bin/uv",
      "args": [
        "--directory",
        "/<your-path>/mcp-server-aws-resources-python",
        "run",
        "src/mcp_server_aws_resources/server.py",
        "--profile",
        "testing"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `aws_resources_query_or_modify` | Выполняет фрагмент boto3 кода для запроса или модификации AWS ресурсов с изолированным выполнением Python |

## Возможности

- Запуск сгенерированного Python кода для запроса любых AWS ресурсов через boto3
- Поддержка операций как только для чтения, так и управления (разрешения зависят от роли AWS пользователя)
- Изолированное выполнение кода с AST-валидацией
- Мультиплатформенная поддержка Docker (Linux/amd64, Linux/arm64, Linux/arm/v7)
- Корректная JSON сериализация с обработкой специфичных для AWS объектов
- Поддержка множественных методов аутентификации AWS (учетные данные, профили, токены сессии)
- Ограниченная среда выполнения с лимитированными встроенными функциями для безопасности

## Переменные окружения

### Обязательные
- `AWS_ACCESS_KEY_ID` - Ваш AWS ключ доступа для аутентификации
- `AWS_SECRET_ACCESS_KEY` - Ваш AWS секретный ключ для аутентификации

### Опциональные
- `AWS_SESSION_TOKEN` - AWS токен сессии при использовании временных учетных данных
- `AWS_DEFAULT_REGION` - AWS регион (по умолчанию 'us-east-1', если не установлен)
- `AWS_PROFILE` - Имя AWS профиля при использовании файла с учетными данными

## Примеры использования

```
Список всех S3 бакетов в моем AWS аккаунте
```

```
Получить последний успешный деплой CodePipeline для конкретного пайплайна
```

```
Запросить DynamoDB таблицы и их конфигурации
```

```
Исправить ошибки разрешений DynamoDB анализируя IAM политики
```

```
Управлять AWS ресурсами через boto3 операции
```

## Ресурсы

- [GitHub Repository](https://github.com/baryhuang/mcp-server-aws-resources-python)

## Примечания

**Внимание**: Этот инструмент позволяет выполнять полные AWS операции, не только для чтения. Разрешения вашей роли AWS пользователя определяют, какие операции вы можете выполнять. Сервер включает функции безопасности, такие как AST-валидация кода и ограниченная среда выполнения. Все фрагменты кода должны устанавливать переменную 'result', которая будет возвращена клиенту.