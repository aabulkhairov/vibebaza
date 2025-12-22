---
title: Unleash Integration (Feature Toggle) MCP сервер
description: MCP сервер, который интегрируется с системой Unleash Feature Toggle, обеспечивая связь между LLM приложениями и управлением feature flag в Unleash.
tags:
- DevOps
- Integration
- API
- Monitoring
author: Community
featured: false
---

MCP сервер, который интегрируется с системой Unleash Feature Toggle, обеспечивая связь между LLM приложениями и управлением feature flag в Unleash.

## Установка

### NPM

```bash
npm i
```

### NPX

```bash
npx -y unleash-mcp
```

### Из исходного кода

```bash
npm run build
npm start
```

## Конфигурация

### Claude Desktop/Cursor

```json
{
  "mcpServers": {
    "unleash": {
      "command": "npx",
      "args": [
        "-y",
        "unleash-mcp"
      ],
      "env": {
        "UNLEASH_URL": "YOUR_UNLEASH_END_POINT",
        "UNLEASH_API_TOKEN": "YOUR_UNLEASH_API_TOKEN",
        "MCP_TRANSPORT": "stdio",
        "MCP_HTTP_PORT": 3001
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get-flag` | Получение feature flag для извлечения статуса отдельного флага |
| `get-projects` | Получение проектов для извлечения всех проектов |

## Возможности

- Проверка статуса feature flag из Unleash
- Предоставление информации о feature flag для LLM
- Создание feature flag
- Обновление feature flag
- Список всех проектов

## Переменные окружения

### Обязательные
- `UNLEASH_URL` - URL вашего Unleash эндпоинта
- `UNLEASH_API_TOKEN` - Ваш Unleash API токен для аутентификации

### Опциональные
- `MCP_TRANSPORT` - Метод транспорта для MCP (stdio или http)
- `MCP_HTTP_PORT` - Номер порта для HTTP транспорта

## Ресурсы

- [GitHub Repository](https://github.com/cuongtl1992/unleash-mcp)

## Примечания

Требует Node.js v18 или выше и TypeScript v5.0 или выше. Необходим доступ к экземпляру сервера Unleash. Сервер поддерживает транспорты STDIO и HTTP/SSE.