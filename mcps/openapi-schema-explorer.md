---
title: OpenAPI Schema Explorer MCP сервер
description: MCP сервер, который предоставляет токен-эффективный доступ к спецификациям OpenAPI (v3.0) и Swagger (v2.0) через MCP Resources, позволяя исследовать API спецификации без загрузки целых файлов в контекст.
tags:
- API
- Code
- Productivity
- Integration
- DevOps
author: kadykov
featured: false
---

MCP сервер, который предоставляет токен-эффективный доступ к спецификациям OpenAPI (v3.0) и Swagger (v2.0) через MCP Resources, позволяя исследовать API спецификации без загрузки целых файлов в контекст.

## Установка

### NPX (Рекомендуется)

```bash
npx -y mcp-openapi-schema-explorer@latest <path-or-url-to-spec>
```

### Docker

```bash
docker run --rm -i kadykov/mcp-openapi-schema-explorer:latest <path-or-url-to-spec>
```

### Глобальная установка

```bash
npm install -g mcp-openapi-schema-explorer
```

### Из исходников

```bash
git clone https://github.com/kadykov/mcp-openapi-schema-explorer.git
cd mcp-openapi-schema-explorer
npm install
npm run build
```

## Конфигурация

### Конфигурация NPX

```json
{
  "mcpServers": {
    "My API Spec (npx)": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-openapi-schema-explorer@latest",
        "<path-or-url-to-spec>",
        "--output-format",
        "yaml"
      ],
      "env": {}
    }
  }
}
```

### Конфигурация Docker для удаленных файлов

```json
{
  "mcpServers": {
    "My API Spec (Docker Remote)": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "kadykov/mcp-openapi-schema-explorer:latest",
        "<remote-url-to-spec>"
      ],
      "env": {}
    }
  }
}
```

### Конфигурация Docker для локальных файлов

```json
{
  "mcpServers": {
    "My API Spec (Docker Local)": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "-v",
        "/full/host/path/to/spec.yaml:/spec/api.yaml",
        "kadykov/mcp-openapi-schema-explorer:latest",
        "/spec/api.yaml",
        "--output-format",
        "yaml"
      ],
      "env": {}
    }
  }
}
```

## Возможности

- Доступ к MCP ресурсам через интуитивные URI (openapi://info, openapi://paths/..., openapi://components/...)
- Поддержка OpenAPI v3.0 и Swagger v2.0 с автоматическим преобразованием v2.0 в v3.0
- Поддержка локальных и удаленных файлов (пути к файлам или HTTP/HTTPS URLs)
- Токен-эффективный дизайн для минимизации использования токенов в LLMs
- Множественные форматы вывода (JSON, YAML, минифицированный JSON)
- Динамическое имя сервера, отражающее info.title из загруженной спецификации
- Трансформация ссылок внутренних $refs в кликабельные MCP URI
- Поддержка многозначных параметров для получения нескольких элементов в одном запросе

## Примеры использования

```
Исследование структуры и деталей API спецификации
```

```
Просмотр API путей и операций
```

```
Изучение компонентных схем и определений
```

```
Получение деталей для конкретных HTTP методов на API путях
```

```
Список доступных компонентов по типу
```

## Ресурсы

- [GitHub Repository](https://github.com/kadykov/mcp-openapi-schema-explorer)

## Примечания

Использует MCP Resources (не инструменты) для исследования данных только для чтения. Поддерживает многозначные параметры с разделенными запятыми значениями (например, get,post). Параметры пути должны быть URL-кодированы. Имя сервера в MCP клиентах отражает название API спецификации.