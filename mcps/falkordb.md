---
title: FalkorDB MCP сервер
description: Сервер для работы с графовой базой данных FalkorDB - получение схемы и чтение/запись через Cypher
tags:
- Storage
- DevOps
- API
- Productivity
- Database
author: FalkorDB
featured: false
---

Сервер для работы с графовой базой данных FalkorDB - получение схемы и чтение/запись через Cypher

## Установка

### Из исходного кода

```bash
git clone https://github.com/falkordb/falkordb-mcpserver.git
   cd falkordb-mcpserver
```

### NPM

```bash
npm install
```

## Переменные окружения

### Обязательные
- `FALKORDB_USERNAME` - Имя пользователя для аутентификации в FalkorDB (если требуется)
- `FALKORDB_PASSWORD` - Пароль для аутентификации в FalkorDB (если требуется)

### Опциональные
- `NODE_ENV` - Окружение (development, production)
- `FALKORDB_HOST` - Хост FalkorDB (по умолчанию: localhost)
- `FALKORDB_PORT` - Порт FalkorDB (по умолчанию: 6379)
- `MCP_API_KEY` - API ключ для аутентификации MCP запросов

## Ресурсы

- [GitHub Repository](https://github.com/FalkorDB/FalkorDB-MCPServer)
- [Documentation](https://www.falkordb.com/)