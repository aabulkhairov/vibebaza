---
title: Stockfish MCP сервер
description: MCP сервер, который обеспечивает связь между AI системами и шахматным движком Stockfish через Model Context Protocol, позволяя анализировать шахматные позиции и оценивать их.
tags:
- AI
- API
- Integration
- Analytics
author: Community
featured: false
---

MCP сервер, который обеспечивает связь между AI системами и шахматным движком Stockfish через Model Context Protocol, позволяя анализировать шахматные позиции и оценивать их.

## Установка

### Из исходного кода

```bash
git clone https://github.com/sonirico/mcp-stockfish
cd mcp-stockfish
make install
```

## Конфигурация

### Claude Desktop

```json
{
  "mcpServers": {
    "chess": {
      "command": "mcp-stockfish",
      "env": {
        "MCP_STOCKFISH_LOG_LEVEL": "info"
      }
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `uci` | Инициализирует движок в режиме UCI |
| `isready` | Проверяет готовность движка. Возвращает readyok |
| `position` | Устанавливает доску в начальную позицию или использует FEN нотацию |
| `go` | Запускает движок для вычисления лучшего хода с опциональными ограничениями по глубине или времени |
| `stop` | Останавливает текущий поиск |
| `quit` | Закрывает сессию |

## Возможности

- Одновременные сессии: Запуск нескольких экземпляров Stockfish одновременно
- Полная поддержка UCI: Поддерживаются все основные UCI команды
- Управление сессиями: Автоматическая очистка и обработка таймаутов
- Формат ответов JSON: Структурированные ответы для всех команд
- Docker готовность: Поддержка контейнерного деплоя
- Режимы HTTP и STDIO: Гибкие режимы работы сервера

## Переменные окружения

### Опциональные
- `MCP_STOCKFISH_SERVER_MODE` - Режим сервера - 'stdio' или 'http' (по умолчанию: 'stdio')
- `MCP_STOCKFISH_HTTP_HOST` - HTTP хост (по умолчанию: 'localhost')
- `MCP_STOCKFISH_HTTP_PORT` - HTTP порт (по умолчанию: 8080)
- `MCP_STOCKFISH_PATH` - Путь к исполняемому файлу Stockfish (по умолчанию: 'stockfish')
- `MCP_STOCKFISH_MAX_SESSIONS` - Максимальное количество одновременных сессий (по умолчанию: 10)
- `MCP_STOCKFISH_SESSION_TIMEOUT` - Таймаут сессии (по умолчанию: '30m')
- `MCP_STOCKFISH_COMMAND_TIMEOUT` - Таймаут команды (по умолчанию: '30s')
- `MCP_STOCKFISH_LOG_LEVEL` - Уровень логирования - debug, info, warn, error, fatal

## Ресурсы

- [GitHub Repository](https://github.com/sonirico/mcp-stockfish)

## Примечания

Требует установленный шахматный движок Stockfish. Параметры инструмента включают 'command' (UCI команда для выполнения) и опциональный 'session_id'. Ответы содержат поля status, session_id, command, массив response и error.