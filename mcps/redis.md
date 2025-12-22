---
title: Redis MCP сервер
description: Реализация сервера Redis Model Context Protocol (MCP), которая позволяет LLM взаимодействовать с хранилищами ключ-значение Redis через стандартизированные инструменты для операций с базой данных.
tags:
- Database
- Storage
- API
- DevOps
- Integration
author: GongRzhe
featured: false
---

Реализация сервера Redis Model Context Protocol (MCP), которая позволяет LLM взаимодействовать с хранилищами ключ-значение Redis через стандартизированные инструменты для операций с базой данных.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @gongrzhe/server-redis-mcp --client claude
```

### NPX

```bash
npx @gongrzhe/server-redis-mcp@1.0.0 redis://your-redis-host:port
```

### NPM Global

```bash
npm install -g @gongrzhe/server-redis-mcp@1.0.0
@gongrzhe/server-redis-mcp redis://your-redis-host:port
```

### Docker

```bash
docker build -t mcp/redis .
```

### Из исходного кода

```bash
npm install
npm run build
```

## Конфигурация

### Claude Desktop (NPX)

```json
{
  "mcpServers": {
    "redis": {
      "command": "npx",
      "args": [
        "@gongrzhe/server-redis-mcp@1.0.0",
        "redis://localhost:6379"
      ]
    }
  }
}
```

### Claude Desktop (Node)

```json
{
  "mcpServers": {
    "redis": {
      "command": "node",
      "args": [
        "path/to/build/index.js",
        "redis://10.1.210.223:6379"
      ]
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "redis": {
      "command": "docker",
      "args": [
        "run", 
        "-i", 
        "--rm", 
        "mcp/redis", 
        "redis://host.docker.internal:6379"
      ]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `set` | Устанавливает пару ключ-значение в Redis с опциональным временем истечения в секундах |
| `get` | Получает значение по ключу из Redis |
| `delete` | Удаляет один или несколько ключей из Redis |
| `list` | Список ключей Redis, соответствующих шаблону (по умолчанию: *) |

## Возможности

- Операции с хранилищем ключ-значение в Redis
- Опциональная установка времени истечения для ключей
- Список и поиск ключей по шаблону
- Поддержка удаления нескольких ключей
- Поддержка Docker контейнера с доступом к сети хоста
- 62 инструмента Redis MCP доступны в ветке redis-plus

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/REDIS-MCP-Server)

## Примечания

Сервер поддерживает конфигурацию Redis URL и по умолчанию использует redis://localhost:6379. Для использования Docker на macOS используйте host.docker.internal, если Redis запущен в сети хоста. Расширенная версия с 62 инструментами Redis MCP доступна в ветке redis-plus.