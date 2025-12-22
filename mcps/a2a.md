---
title: A2A MCP сервер
description: MCP сервер-мост между Model Context Protocol (MCP) и Agent-to-Agent (A2A)
  протоколом. Позволяет AI-ассистентам (вроде Claude) взаимодействовать с A2A агентами
  через единый интерфейс.
tags:
- AI
- Integration
- API
- Messaging
- Productivity
author: GongRzhe
featured: true
install_command: npx -y @smithery/cli install @GongRzhe/A2A-MCP-Server --client claude
---

MCP сервер-мост между Model Context Protocol (MCP) и Agent-to-Agent (A2A) протоколом. Позволяет AI-ассистентам (вроде Claude) взаимодействовать с A2A агентами через единый интерфейс.

## Установка

### Smithery

```bash
npx -y @smithery/cli install @GongRzhe/A2A-MCP-Server --client claude
```

### PyPI

```bash
pip install a2a-mcp-server
```

### Из исходников

```bash
git clone https://github.com/GongRzhe/A2A-MCP-Server.git
cd A2A-MCP-Server
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### Командная строка

```bash
uvx a2a-mcp-server
```

## Конфигурация

### Claude Desktop (PyPI)

```json
{
  "mcpServers": {
    "a2a": {
      "command": "uvx",
      "args": [
        "a2a-mcp-server"
      ]
    }
  }
}
```

### Claude Desktop (локально)

```json
{
  "a2a": {
    "command": "C:\\path\\to\\python.exe",
    "args": [
      "C:\\path\\to\\A2A-MCP-Server\\a2a_mcp_server.py"
    ],
    "env": {
      "MCP_TRANSPORT": "stdio",
      "PYTHONPATH": "C:\\path\\to\\A2A-MCP-Server"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------------|----------|
| `register_agent` | Зарегистрировать A2A агента на сервере-мосте |
| `list_agents` | Получить список всех зарегистрированных агентов |
| `unregister_agent` | Удалить A2A агента с сервера-моста |
| `send_message` | Отправить сообщение агенту и получить task_id ответа |
| `send_message_stream` | Отправить сообщение и стримить ответ |
| `get_task_result` | Получить результат задачи по её ID |
| `cancel_task` | Отменить запущенную задачу |

## Возможности

- Регистрация A2A агентов на сервере-мосте
- Просмотр всех зарегистрированных агентов
- Удаление агентов при необходимости
- Отправка сообщений A2A агентам и получение ответов
- Стриминг ответов от A2A агентов в реальном времени
- Отслеживание какой A2A агент обрабатывает какую задачу
- Получение результатов задач по ID
- Отмена запущенных задач
- Несколько типов транспорта: stdio, streamable-http, SSE

## Переменные окружения

### Опциональные
- `MCP_TRANSPORT` — тип транспорта: stdio, streamable-http или sse
- `MCP_HOST` — хост MCP сервера
- `MCP_PORT` — порт MCP сервера (для HTTP транспортов)
- `MCP_PATH` — путь к эндпоинту MCP сервера (для HTTP транспортов)
- `MCP_SSE_PATH` — путь к SSE эндпоинту (для SSE транспорта)
- `MCP_DEBUG` — включить отладочное логирование

## Примеры использования

```
I need to register a new agent. Can you help me with that? (Agent URL: http://localhost:41242)
```

```
Ask the agent at http://localhost:41242 what it can do.
```

```
Can you get the results for task ID: 550e8400-e29b-41d4-a716-446655440000?
```

```
What's the exchange rate from USD to EUR?
```

```
Register an agent at http://localhost:41242
```

## Ресурсы

- [GitHub Repository](https://github.com/GongRzhe/A2A-MCP-Server)

## Примечания

Поддерживает несколько MCP клиентов: Claude (веб и десктоп), Cursor IDE, Windsurf Browser. Сервер работает как мост между MCP и A2A протоколами, позволяя управлять задачами и общаться с A2A агентами в реальном времени. Включает скрипт config_creator.py для автоматической настройки Claude Desktop.
