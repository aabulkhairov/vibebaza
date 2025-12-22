---
title: Tyk API Management MCP сервер
description: Инструмент для создания MCP серверов из спецификаций OpenAPI/Swagger, который позволяет AI-ассистентам взаимодействовать с REST API, преобразуя OpenAPI спецификации в MCP инструменты.
tags:
- API
- Integration
- DevOps
- Productivity
- Code
author: TykTechnologies
featured: false
---

Инструмент для создания MCP серверов из спецификаций OpenAPI/Swagger, который позволяет AI-ассистентам взаимодействовать с REST API, преобразуя OpenAPI спецификации в MCP инструменты.

## Установка

### NPX

```bash
npx -y @tyktechnologies/api-to-mcp --spec https://petstore3.swagger.io/api/v3/openapi.json
```

### Из исходного кода

```bash
git clone <repository-url>
cd openapi-to-mcp-generator
npm install
npm run build
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "api-tools": {
      "command": "npx",
      "args": [
        "-y",
        "@tyktechnologies/api-to-mcp",
        "--spec",
        "https://petstore3.swagger.io/api/v3/openapi.json"
      ],
      "enabled": true
    }
  }
}
```

### Cursor

```json
{
  "servers": [
    {
      "command": "npx",
      "args": [
        "-y",
        "@tyktechnologies/api-to-mcp",
        "--spec",
        "./path/to/your/openapi.json"
      ],
      "name": "My API Tools"
    }
  ]
}
```

## Возможности

- Динамическая загрузка OpenAPI спецификаций из файла или HTTP/HTTPS URL
- Поддержка OpenAPI Overlays, загружаемых из файлов или HTTP/HTTPS URL
- Настраиваемое сопоставление OpenAPI операций с MCP инструментами
- Продвинутая фильтрация операций с использованием glob паттернов как для operationId, так и для URL путей
- Комплексная обработка параметров с сохранением формата и метаданных расположения
- Обработка аутентификации API
- Метаданные OpenAPI (название, версия, описание) используются для конфигурации MCP сервера
- Иерархические резервные описания (описание операции → краткое описание операции → краткое описание пути)
- Поддержка пользовательских HTTP заголовков через переменные окружения и CLI
- X-MCP заголовок для отслеживания и идентификации API запросов

## Переменные окружения

### Опциональные
- `OPENAPI_SPEC_PATH` - Путь к файлу OpenAPI спецификации
- `OPENAPI_OVERLAY_PATHS` - Разделенные запятыми пути к файлам overlay JSON
- `TARGET_API_BASE_URL` - Базовый URL для API вызовов (переопределяет OpenAPI серверы)
- `MCP_WHITELIST_OPERATIONS` - Разделенный запятыми список ID операций или URL путей для включения (поддерживает glob паттерны)
- `MCP_BLACKLIST_OPERATIONS` - Разделенный запятыми список ID операций или URL путей для исключения (поддерживает glob паттерны)
- `API_KEY` - API ключ для целевого API (если требуется)
- `SECURITY_SCHEME_NAME` - Название схемы безопасности, требующей API ключ
- `SECURITY_CREDENTIALS` - JSON строка, содержащая учетные данные безопасности для множественных схем

## Примеры использования

```
List all available pets in the pet store using the API
```

## Ресурсы

- [GitHub Repository](https://github.com/TykTechnologies/tyk-dashboard-mcp)

## Примечания

Настройки конфигурации применяются в порядке приоритета: параметры командной строки, переменные окружения, затем файл конфигурации JSON. Сервер может использоваться с Vercel AI SDK для прямой интеграции с JavaScript/TypeScript. Вы можете сделать форк этого репозитория и настроить его для создания брендированных MCP серверов для конкретных API.