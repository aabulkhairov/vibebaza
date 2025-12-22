---
title: XiYan MCP сервер
description: MCP сервер, который позволяет делать запросы к базам данных MySQL и PostgreSQL на естественном языке, используя XiYan-SQL — передовую модель text-to-SQL для преобразования естественного языка в SQL запросы.
tags:
- Database
- AI
- Analytics
- Integration
author: XGenerationLab
featured: true
---

MCP сервер, который позволяет делать запросы к базам данных MySQL и PostgreSQL на естественном языке, используя XiYan-SQL — передовую модель text-to-SQL для преобразования естественного языка в SQL запросы.

## Установка

### pip

```bash
pip install xiyan-mcp-server
```

### Из исходного кода

```bash
pip install git+https://github.com/XGenerationLab/xiyan_mcp_server.git
```

### Smithery.ai

```bash
@XGenerationLab/xiyan_mcp_server
```

## Конфигурация

### Claude Desktop

```json
{
    "mcpServers": {
        "xiyan-mcp-server": {
            "command": "/xxx/python",
            "args": [
                "-m",
                "xiyan_mcp_server"
            ],
            "env": {
                "YML": "PATH/TO/YML"
            }
        }
    }
}
```

### Cursor (stdio)

```json
{
  "mcpServers": {
    "xiyan-mcp-server": {
      "command": "/xxx/python",
      "args": [
        "-m",
        "xiyan_mcp_server"
      ],
      "env": {
        "YML": "path/to/yml"
      }
    }
  }
}
```

### Cursor (SSE)

```json
{
  "mcpServers": {
    "xiyan_mcp_server_1": {
      "url": "http://localhost:8000/sse"
    }
  }
}
```

## Доступные инструменты

| Инструмент | Описание |
|------|-------------|
| `get_data` | Предоставляет интерфейс на естественном языке для получения данных из базы данных путем преобразования естественного языка... |

## Возможности

- Получение данных на естественном языке через XiYanSQL
- Поддержка обычных LLM (GPT, qwenmax) и передовых Text-to-SQL моделей
- Поддержка полностью локального режима (высокая безопасность!)
- Поддержка баз данных MySQL и PostgreSQL
- Список доступных таблиц в качестве ресурсов
- Чтение содержимого таблиц
- Поддержка протоколов транспорта stdio и SSE

## Переменные окружения

### Обязательные
- `YML` - Путь к YAML файлу конфигурации, содержащему настройки модели и базы данных

## Ресурсы

- [GitHub Repository](https://github.com/XGenerationLab/xiyan_mcp_server)

## Примечания

Требует Python 3.11+. Необходим YAML файл конфигурации с настройками модели и базы данных. Поддерживает удаленный режим (требует API ключ) и локальный режим (более безопасный). Модель XiYanSQL достигает передовых результатов на бенчмарке Bird для задач text-to-SQL.