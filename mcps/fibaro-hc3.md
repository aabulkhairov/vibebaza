---
title: Fibaro HC3 MCP сервер
description: MCP сервер, который обеспечивает бесшовную интеграцию между LLM приложениями и системами умного дома Fibaro Home Center 3, позволяя AI помощникам управлять устройствами и выполнять сценарии автоматизации через команды на естественном языке.
tags:
- Integration
- API
- Productivity
- Monitoring
author: coding-sailor
featured: false
---

MCP сервер, который обеспечивает бесшовную интеграцию между LLM приложениями и системами умного дома Fibaro Home Center 3, позволяя AI помощникам управлять устройствами и выполнять сценарии автоматизации через команды на естественном языке.

## Установка

### Из исходников

```bash
# Install dependencies
npm install

# Build the TypeScript code
npm run build
```

### Docker

```bash
# Build and start the container
docker-compose up -d
```

## Конфигурация

### Claude Desktop (STDIO)

```json
{
  "mcpServers": {
    "mcp-server-hc3": {
      "command": "node",
      "args": ["/path/to/your/mcp-server-hc3/dist/index.js"],
      "env": {
        "HC3_HOST": "192.168.1.100",
        "HC3_USERNAME": "admin",
        "HC3_PASSWORD": "your_password",
        "HC3_PORT": "80",
        "MCP_TRANSPORT_TYPE": "stdio"
      }
    }
  }
}
```

### Claude Desktop (Docker)

```json
{
  "mcpServers": {
    "mcp-server-hc3": {
      "command": "curl",
      "args": ["-X", "POST", "-H", "Content-Type: application/json", "-H", "x-api-key: your-api-key-here", "http://localhost:3000/mcp"]
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `list_rooms` | Получить все комнаты в вашей HC3 системе |
| `get_room` | Получить детальную информацию о конкретной комнате |
| `list_devices` | Список устройств с опциональной фильтрацией |
| `get_device` | Получить полную информацию об устройстве |
| `call_device_action` | Выполнить любое действие устройства (turnOn, turnOff, toggle, setValue и т.д.) |
| `list_scenes` | Получить все сценарии в вашей HC3 системе |
| `get_scene` | Получить детальную информацию о конкретном сценарии |
| `execute_scene` | Выполнить сценарий (асинхронно или синхронно) |
| `kill_scene` | Остановить выполняющийся сценарий |
| `test_connection` | Тестировать подключение к вашей HC3 системе |

## Возможности

- Прямое управление устройствами умного дома Fibaro HC3 через естественный язык
- Управление комнатами и фильтрация устройств
- Выполнение сценариев и управление ими
- Поддержка STDIO и HTTP методов транспорта
- Поддержка деплоя через Docker
- API key аутентификация для HTTP транспорта
- MCP Inspector для разработки и отладки
- Интеграция с официальным Fibaro HC3 REST API

## Переменные окружения

### Обязательные
- `HC3_HOST` - IP адрес или имя хоста HC3
- `HC3_USERNAME` - имя пользователя HC3
- `HC3_PASSWORD` - пароль HC3

### Опциональные
- `HC3_PORT` - HTTP порт HC3
- `SERVER_TIMEOUT` - таймаут запроса в мс
- `LOG_LEVEL` - уровень логирования
- `MCP_TRANSPORT_TYPE` - тип транспорта: 'stdio' или 'http'
- `MCP_HTTP_HOST` - адрес привязки HTTP сервера
- `MCP_HTTP_PORT` - порт HTTP сервера
- `MCP_HTTP_API_KEY` - API ключ для HTTP аутентификации

## Примеры использования

```
Turn on all lights in the living room
```

```
Toggle main kitchen lamp
```

```
Execute my goodnight scene
```

```
Set bedroom lamp to 10%
```

## Ресурсы

- [GitHub Repository](https://github.com/coding-sailor/mcp-server-hc3)

## Примечания

Это решение, разработанное сообществом, не связанное с Fibaro. Требует систему Fibaro Home Center 3. Поддерживает STDIO и HTTP методы транспорта. Никогда не коммитьте ваш .env файл в систему контроля версий. При использовании HTTP транспорта настоятельно рекомендуется API key аутентификация для безопасности.