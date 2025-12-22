---
title: OpenAPI MCP сервер
description: Сервер Model Context Protocol, который позволяет искать и исследовать OpenAPI спецификации через oapis.org, предоставляя обзор и подробную информацию об операциях API.
tags:
- API
- Search
- Integration
- Code
- DevOps
author: janwilmake
featured: true
---

Сервер Model Context Protocol, который позволяет искать и исследовать OpenAPI спецификации через oapis.org, предоставляя обзор и подробную информацию об операциях API.

## Установка

### Установить этот MCP

```bash
https://installthismcp.com/OpenAPI%20MCP%20Server?url=https%3A%2F%2Fopenapi-mcp.openapisearch.com%2Fmcp
```

### MCP URL

```bash
https://openapi-mcp.openapisearch.com/mcp
```

### Локальная разработка

```bash
wrangler dev
```

### MCP Inspector

```bash
npx @modelcontextprotocol/inspector
```

## Возможности

- Получение обзора любой OpenAPI спецификации
- Извлечение деталей о конкретных операциях API
- Поддержка форматов JSON и YAML
- Протестировано с Claude Desktop и Cursor
- 3-шаговый процесс: определяет идентификатор OpenAPI, запрашивает резюме на простом языке, определяет нужные эндпоинты

## Ресурсы

- [GitHub Repository](https://github.com/snaggle-ai/openapi-mcp-server)

## Примечания

Сервер работает через 3-шаговый процесс: определение необходимого идентификатора OpenAPI, запрос резюме на простом языке и определение того, какие эндпоинты нужны с подробными объяснениями. Связанные проекты включают OpenAPISearch и OAPIS от того же автора.