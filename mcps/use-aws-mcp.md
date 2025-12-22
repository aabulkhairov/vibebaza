---
title: use_aws_mcp сервер
description: Автономный Model Context Protocol сервер, который предоставляет функциональность AWS CLI через стандартизированный интерфейс, воспроизводя инструмент use_aws из Amazon Q Developer CLI для использования в различных AI инструментах.
tags:
- Cloud
- DevOps
- API
- Integration
- Productivity
author: Community
featured: false
---

Автономный Model Context Protocol сервер, который предоставляет функциональность AWS CLI через стандартизированный интерфейс, воспроизводя инструмент use_aws из Amazon Q Developer CLI для использования в различных AI инструментах.

## Установка

### Cargo Install

```bash
cargo install use_aws_mcp
```

### Из исходных кодов

```bash
cargo build --release
```

## Конфигурация

### Конфигурация MCP клиента

```json
{
  "mcpServers": {
    "use_aws_mcp": {
      "name": "use_aws_mcp",
      "command": "use_aws_mcp",
      "timeout": 300,
      "env": {},
      "disabled": false
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `use_aws` | Выполнение команд AWS CLI с правильной обработкой параметров и проверками безопасности |

## Возможности

- Интеграция с AWS CLI с правильной обработкой параметров
- Проверки безопасности с автоматическим определением операций только для чтения и операций записи
- Управление User Agent для правильной настройки AWS CLI user agent
- Форматирование параметров с автоматическим преобразованием в kebab-case
- Комплексная обработка ошибок и форматирование вывода
- Удобочитаемые описания с использованием форматирования терминала
- Обрезка вывода для больших ответов (максимум 100KB)

## Переменные окружения

### Опциональные
- `AWS_DEFAULT_PROFILE` - AWS профиль для использования учетных данных
- `RUST_LOG` - Включить отладочное логирование (установить в use_aws=debug)

## Примеры использования

```
List my S3 buckets
```

```
Describe EC2 instances in us-west-2
```

```
List Lambda functions using development profile
```

```
Get information about AWS resources across different services
```

## Ресурсы

- [GitHub Repository](https://github.com/runjivu/use_aws_mcp)

## Примечания

Требует установленный и настроенный AWS CLI с правильными учетными данными. MCP клиенты без shell, такие как Cursor, могут потребовать явного указания AWS профиля. Операции только для чтения автоматически определяются и не требуют подтверждения пользователя.